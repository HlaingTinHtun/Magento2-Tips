# Magento2-Tips
## Tips from migrating mage2 from mage1

The usages I found in magento-1 `Gold Export Module` that need to upgrade
- Mage::getBaseDir
- Mage::log
- Mage::getModel
Mage static method is deprecated at mageno2.
Magento2, not using factory Patten types like Mage::getModel ,Mage::getsingleton() etc
Using class nameSpace concept can see further more in below
https://magento.stackexchange.com/questions/128497/class-mage-not-found-in-magento-2

What I found to upgrade the Mage static method in mage2
- For Dir 
    Mage:getBaseDir => require __DIR__
- For Logging
Magento 1 used static method Mage::log() with the required file name and text. However, we are no longer able to do the same in Magento 2 — it uses Monolog as the main logging tool which follows the logging standard of PSR-3 . Monolog doesn’t allow to set a new filepath where you want to log a message. 
See Further more 
https://belvg.com/blog/using-virtual-types-for-saving-custom-logs-in-magento-2-0.html
- For Model Connection
For the Mage::model
I found out two ways (Constructor Injection For Repository Interfaces and Using Object Manager Directly from our classes)
I still not sure which one is the best and suitable one for us. Most of the developers prefer using Factories and Interfaces. They don’t recommend using objectManager directly. See Further more
https://magento.stackexchange.com/questions/117098/magento-2-to-use-or-not-to-use-the-objectmanager-directly

These are what I found out while I am researching (Just Sharing My Few Knowledge). Please let me know if I was wrong something.
