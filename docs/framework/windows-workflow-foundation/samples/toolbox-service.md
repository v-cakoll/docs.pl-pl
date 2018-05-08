---
title: Usługi przybornika
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b3ea56d28d202bd8356fea1783b6675a708631d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="toolbox-service"></a>Usługi przybornika
W tym przykładzie pokazano, jak zaktualizować [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] przybornika działań na podstawie kontekstu przepływu pracy. Próbka zawiera przepływ pracy, który zmieni zawartość przybornika według tego, czy wybrano działania niestandardowego.  
  
## <a name="discussion"></a>Omówienie  
 Podczas tworzenia przepływu pracy, klienci mają zazwyczaj ich przybornika być kontekstowa. Użytkownik może na przykład chcesz upewnij się, że przybornika zawiera kilka dodatkowych czynności, po dodaniu określonego działania do przepływu pracy. Jeśli działania są usuwane z przepływu pracy, przybornika powinien zareagować odpowiednio zależnie od wymagań domeny.  
  
 W Projektancie ponownie hostowanej przepływu pracy kontrolować formant z przybornika i zapewnić, że na podstawie zmian modelu w przepływie pracy, host wyzwala odpowiednie zmiany w formancie przybornika. Jednak w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], przybornika nie są kontrolowane przez użytkownika i w związku z tym interfejsem jest wymagany do modyfikowania jej zawartości. `IActivityToolboxService` jest ten interfejs.  
  
 Interfejs API udostępnia następujące cztery metody.  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WorkflowSimulator.sln.  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Otwórz plik Workflow.xaml.  
  
4.  Dodaj **CustomActivity** przez przeciąganie i upuszczanie go z przybornika. Należy zauważyć, że wywoływana dodatkowych kategorii przybornika: **nową kategorię WF** z działaniem dodatkowe **przypisać**.  
  
5.  Teraz, usuń zaznaczenie **CustomActivity** przeciągając go do niego innego działania.  
  
6.  Element **przypisać** w kategorii **nową kategorię WF** teraz jest usuwany w przyborniku. Ponadto ponieważ nie ma więcej elementów w kategorii, kategorię spowoduje usunięcie również.  
  
7.  Wybierz **CustomActivity** ponownie i kategorii i **przypisać** działania jest ponownie dodane.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
