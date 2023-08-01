Model Classes
+++++++++++++++
.. _classes:

Class Description
=================
 ============== ====================== ========= =========================================== ================ ====================================================================================== 
  Class Name     Common Name            AphiaID   URN                                         Grouping         Description                                                                           
 ============== ====================== ========= =========================================== ================ ====================================================================================== 
  Akashiwo       Akashiwo sanguinea     232546    urn:lsid:marinespecies.org:taxname:232546   Dinoflagellate   Monophyletic, marine dinoflagellate                                                   
  Centric        Centric Diatom         148899    urn:lsid:marinespecies.org:taxname:148899   Diatom           Catch-all group of round and difficult to identify diatoms. See images for examples.  
  NanoP_less10   Small cells, > 10 um                                                                                                                                                                
 ============== ====================== ========= =========================================== ================ ====================================================================================== 

Class-Specific Thresholds
=========================
.. _thresholds:

Class-specific thresholds are an important processing step for accounting for bias in the training dataset. Nonuniformity in the training data reflect both practical desicions made by the creators of the data set and the natural distribution of observered phytoplankton classes. In plain terms, the result is that the model is more likely to guess that something belongs to the more commonly observed classes. In that case, we require a high threshold in that predication in order to assign confidence. Conversely when a less common class is observed, it makes sense to have a lower threshold to assign confidence.

Thresholds can be generated for each class by incrementally increasing a threshold from 0 to 1 and calculating the resulting metrics. In this case, the F-score was used to balance recall and percision. The threshold values where F-score begins to decrease 