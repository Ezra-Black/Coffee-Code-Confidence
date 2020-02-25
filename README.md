# Coffee-Code-Confidence

import Foundation
import CoreData


class CoreDataStack {
    
    //can only be one instance of this class ever/Singleton
    static let shared = CoreDataStack()
    
    //gets called once
    lazy var container: NSPersistentContainer = {
        let newContainer = NSPersistentContainer(name: "Journal")
        newContainer.loadPersistentStores { (_, error) in
            guard error == nil else {
                fatalError("Failed to load persistent stores: \(error!)")
            }
        }
        return newContainer
    }()
    
    var mainContext: NSManagedObjectContext {
        return container.viewContext
    }
    
}

