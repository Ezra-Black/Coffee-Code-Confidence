# Coffee-Code-Confidence

<span class="keyword">import</span> Foundation
<span class="keyword">import</span> CoreData


<span class="keyword">class</span> CoreDataStack {
    
    <span class="comment">//can only be one instance of this class ever/Singleton</span>
    <span class="keyword">static let</span> shared = <span class="type">CoreDataStack</span>()
    
    <span class="comment">//gets called once</span>
    <span class="keyword">lazy var</span> container: <span class="type">NSPersistentContainer</span> = {
        <span class="keyword">let</span> newContainer = <span class="type">NSPersistentContainer</span>(name: <span class="string">"Journal"</span>)
        newContainer.<span class="call">loadPersistentStores</span> { (<span class="keyword">_</span>, error) <span class="keyword">in
            guard</span> error == <span class="keyword">nil else</span> {
                <span class="call">fatalError</span>(<span class="string">"Failed to load persistent stores:</span> \(error!)<span class="string">"</span>)
            }
        }
        <span class="keyword">return</span> newContainer
    }()
    
    <span class="keyword">var</span> mainContext: <span class="type">NSManagedObjectContext</span> {
        <span class="keyword">return</span> container.<span class="property">viewContext</span>
    }
    
}
