---
title: Kontrola drzewa działań
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 692f36d993c3f9c27839122b388a24d0698a2b59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183039"
---
# <a name="activity-tree-inspection"></a>Kontrola drzewa działań
Inspekcja drzewa działań jest używana przez autorów aplikacji przepływu pracy do sprawdzania przepływów pracy hostowanych przez aplikację. Za <xref:System.Activities.WorkflowInspectionServices>pomocą , przepływy pracy można wyszukiwać dla określonych działań podrzędnych, poszczególne działania i ich właściwości mogą być wyliczane, a metadane środowiska wykonawczego działań mogą być buforowane w określonym czasie. Ten temat zawiera <xref:System.Activities.WorkflowInspectionServices> omówienie i jak go używać do sprawdzania drzewa działań.  
  
## <a name="using-workflowinspectionservices"></a>Korzystanie z usług inspection przepływu pracy  
 Metoda <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> jest używana do wyliczenia wszystkich działań w określonym drzewie działań. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>zwraca wyliczalne, który dotyka wszystkich działań w drzewie, w tym obrażeń podrzędnych, obsługi delegata, zmiennych domyślnych i wyrażeń argumentów. W poniższym przykładzie definicja przepływu pracy <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.While>jest <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.WriteLine>tworzona przy użyciu , , , i wyrażeń. Po utworzeniu definicji przepływu pracy jest wywoływana, a następnie `InspectActivity` wywoływana jest metoda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Aby wyliczyć działania, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> jest wywoływana na działanie główne i ponownie cyklicznie na każde zwrócone działanie. W poniższym przykładzie <xref:System.Activities.Activity.DisplayName%2A> każdego działania i wyrażenia w drzewie działań jest zapisywany w konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Ten przykładowy kod zawiera następujące dane wyjściowe.  
  
 **Pozycja 1 wykazu**  
**Pozycja 2**
**Lista Pozycja 3**
Pozycja lista**4**
**Pozycja lista 5**
Przedmioty dodane do**kolekcji.** 
 **Sekwencja** **literalnej\<<>>listy**  
 **Podczas**  
 **>ciągu addtocollection\<**  
 **>><ICollection\<String VariableValue**  
 **LambdaValue\<string>**  
 **>>>>ciągu listy locationreferenceValue<List\<**  
 **LambdaValue\<>logiczne**  
 **>>>>ciągu listy locationreferenceValue<List\<**  
 **ForEach\<>smyczkowy**  
 **VariableValue<IEnumerable\<String>>**  
 **WriteLine**  
 **DelegateArgumentValue\<String>**  
 **Sequence**  
 **WriteLine**  
 **Literał\<string>** Aby pobrać określone działanie zamiast wyliczania wszystkich działań, <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> jest używany. Zarówno <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> i wykonać buforowanie `WorkflowInspectionServices.CacheMetadata` metadanych, jeśli nie został wcześniej wywołany. Jeśli <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> został wywołany następnie <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> opiera się na istniejących metadanych. W związku z tym jeśli zmiany drzewa <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>zostały <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> wprowadzone od ostatniego wywołania do , może dać nieoczekiwane wyniki. Jeśli po wywołaniu <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>wprowadzono zmiany w przepływie pracy, metadane <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> można ponownie buforować, wywołując metodę. Buforowanie metadanych jest omówione w następnej sekcji.  
  
### <a name="caching-metadata"></a>Buforowanie metadanych  
 Buforowanie metadanych dla działania tworzy i sprawdza poprawność opisu działania argumenty, zmienne, działania podrzędne i delegatów działania. Metadane, domyślnie, jest buforowany przez środowisko wykonawcze, gdy działanie jest przygotowane do wykonania. Jeśli autor hosta przepływu pracy chce buforować metadane dla drzewa działań lub działań przed <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> tym, na przykład do podjęcia wszystkich kosztów z góry, a następnie może służyć do buforowania metadanych w żądanym czasie.
