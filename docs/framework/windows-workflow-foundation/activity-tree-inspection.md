---
title: Kontrola drzewa działań
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 014795b79b3536b387096e4de64266e26649da21
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705496"
---
# <a name="activity-tree-inspection"></a>Kontrola drzewa działań
Kontrola drzewa działań jest używany przez autorów aplikacji przepływu pracy do wglądu w przepływach pracy obsługiwanych przez aplikację. Za pomocą <xref:System.Activities.WorkflowInspectionServices>, przepływy pracy mogą być wyszukiwane podrzędny określonego działania, poszczególne działania mogą być wyliczane ich właściwości i metadanych środowiska wykonawczego, działania mogą być buforowane w określonym czasie. Ten temat zawiera omówienie <xref:System.Activities.WorkflowInspectionServices> i jak z niej korzystać, aby sprawdzić działanie drzewa.  
  
## <a name="using-workflowinspectionservices"></a>Za pomocą WorkflowInspectionServices  
 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Metoda jest używana, można wyliczyć wszystkie działania w drzewie określonego działania. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Zwraca moduł wyliczający, który dotyka wszystkim działaniom w drzewie, łącznie z elementami podrzędnymi, procedury obsługi delegata, zmiennej wartości domyślne i wyrażenia argumentu. W poniższym przykładzie definicji przepływu pracy jest tworzona przy użyciu <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>i wyrażeń. Po utworzeniu definicji przepływu pracy jest wywoływana, a następnie `InspectActivity` metoda jest wywoływana.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Aby wyliczyć działań, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> nosi nazwę na działania głównego i ponownie rekursywnie dla każdego zwróconego działanie. W poniższym przykładzie <xref:System.Activities.Activity.DisplayName%2A> każdego działania i wyrażenia w działaniu drzewa jest wyświetlony w konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Ten przykładowy kod zawiera następujące dane wyjściowe.  
  
 **Element listy 1**  
**Element listy 2**   
**Element listy 3**   
**Element listy 4**   
**Element listy 5**   
**Elementy dodane do kolekcji.**   
**Sekwencja**   
 **Literał < lista\<ciągu >>**  
 **While**  
 **AddToCollection\<ciąg >**  
 **VariableValue < ICollection\<ciągu >>**  
 **LambdaValue\<String>**  
 **LocationReferenceValue < lista\<ciągu >>**  
 **LambdaValue\<Boolean>**  
 **LocationReferenceValue < lista\<ciągu >>**  
 **Instrukcja ForEach\<ciąg >**  
 **VariableValue < IEnumerable\<ciągu >>**  
 **WriteLine**  
 **DelegateArgumentValue\<String>**  
 **Sequence**  
 **WriteLine**  
 **Literał\<ciągu >** można pobrać określonego działania zamiast wszystkie działania, wyliczanie <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> jest używany. Zarówno <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> i <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> buforowanie metadanych, jeśli `WorkflowInspectionServices.CacheMetadata` nie został wcześniej wywołany. Jeśli <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> następnie wywoływana <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> opiera się na istniejących metadanych. W związku z tym jeśli drzewo zostały zmienione od czasu ostatniego wywołania do <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> może dać nieoczekiwane wyniki. Jeśli wprowadzono zmiany w przepływie pracy po wywołaniu <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, metadane, które mogą być ponownie buforowane przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metody. Buforowanie metadanych została omówiona w następnej sekcji.  
  
### <a name="caching-metadata"></a>Buforowanie metadanych  
 Buforowanie metadanych dla działania kompilacji i weryfikuje opis argumentów tego działania, zmienne, działania podrzędne i działania delegatach. Metadane, domyślnie jest buforowany przez środowisko uruchomieniowe podczas działania jest gotowy do wykonania. Jeśli autor hosta przepływu pracy chce pamięci podręcznej metadanych dla działania lub drzewa działania przed tym, na przykład do podejmowania wszelkich kosztów ponoszonych z góry kosztów, następnie <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> może służyć do na żądany czas w pamięci podręcznej metadanych.
