---
title: Usługa przybornika
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b21f10c763f3f82591f947eb4cc48cf90f4ac79
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406465"
---
# <a name="toolbox-service"></a>Usługa przybornika
W tym przykładzie pokazano, jak zaktualizować [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] przybornika działań na podstawie kontekstu przepływu pracy. Przykładowy zawiera przepływ pracy, który zmiany zawartości przybornika oparte na tego, czy wybrano działań niestandardowych.  
  
## <a name="discussion"></a>Dyskusja  
 Podczas tworzenia przepływu pracy, klienci mają zazwyczaj ich przybornika, aby być kontekstowa. Na przykład użytkownik może chcieć upewnij się, że przybornika określonego działania jest dodawany do przepływu pracy, zawiera kilka dodatkowych działań. Jeśli działania są usuwane z przepływu pracy, przyborniku powinien reagować odpowiednio w zależności od wymagań domeny.  
  
 W Projektancie ponownie hostowanej przepływu pracy możesz kontrolować kontrolki przybornika i upewnij się, że na podstawie zmian modelu w przepływie pracy, host wyzwala odpowiednie zmiany w kontrolki przybornika. Jednak w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], przybornik nie są kontrolowane przez użytkownika i w związku z tym interfejsem jest wymagany do modyfikowania jego zawartości. `IActivityToolboxService` jest ten interfejs.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WorkflowSimulator.sln.  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Otwórz plik Workflow.xaml.  
  
4.  Dodaj **CustomActivity** , przeciągając i upuszczając go z przybornika. Należy zauważyć, że wywoływana dodatkowych kategorii przybornika: **nową kategorię WF** z działaniem dodatkowe **przypisać**.  
  
5.  Teraz, usuń zaznaczenie **CustomActivity** , przeciągając innego działania do niego.  
  
6.  Element **przypisać** w kategorii **nową kategorię WF** w przyborniku zostało usunięte. Ponadto ponieważ istnieje więcej elementów w kategorii, kategorii spowoduje usunięcie również.  
  
7.  Wybierz **CustomActivity** ponownie i kategorii i **przypisać** działanie zostanie ponownie dodany.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
