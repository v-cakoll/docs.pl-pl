---
title: "Działania kontroli drzewa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 91f706b527551bd66bfa18dc926f9453ea9b30fe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="activity-tree-inspection"></a>Działania kontroli drzewa
Działanie drzewa kontroli jest używany przez autorów aplikacji przepływu pracy do zbadania przepływów pracy obsługiwanych przez aplikację. Za pomocą <xref:System.Activities.WorkflowInspectionServices>, przepływy pracy mogą być wyszukiwane działań podrzędnych określonych, poszczególne działania mogą być wyliczane ich właściwości i mogą być buforowane metadane środowiska wykonawczego działań w określonym czasie. Ten temat zawiera omówienie <xref:System.Activities.WorkflowInspectionServices> i jak z niego korzystać do zbadania drzewem działań.  
  
## <a name="using-workflowinspectionservices"></a>Przy użyciu WorkflowInspectionServices  
 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Metoda jest używana do wszystkich działań w drzewie określonego działania. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>Zwraca moduł wyliczający, który go dotyka wszystkie działania w obrębie drzewa, w tym elementy podrzędne, obsługi delegata, zmiennej wartości domyślne i wyrażenia argumentów. W poniższym przykładzie definicji przepływu pracy jest tworzona przy użyciu <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>i wyrażenia. Po utworzeniu definicji przepływu pracy jest wywoływana, a następnie `InspectActivity` metoda jest wywoływana.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Aby wyliczyć działań, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> jest wywoływana na działanie główne i ponownie rekursywnie na każde działanie zwrócony. W poniższym przykładzie <xref:System.Activities.Activity.DisplayName%2A> każdego działania i wyrażenia w działaniu drzewa jest wyświetlony w konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Ten przykładowy kod zawiera następujące dane wyjściowe.  
  
 **Element listy 1**  
**Element listy 2**   
**Element listy 3**   
**Element listy 4**   
**Element listy 5**   
**Elementy dodane do kolekcji.**   
**Sekwencja**   
 **Literał < lista\<ciąg >>**  
 **While**  
 **AddToCollection\<ciąg >**  
 **VariableValue < ICollection\<ciąg >>**  
 **LambdaValue\<ciąg >**  
 **LocationReferenceValue < lista\<ciąg >>**  
 **LambdaValue\<wartość logiczna >**  
 **LocationReferenceValue < lista\<ciąg >>**  
 **Instrukcja ForEach\<ciąg >**  
 **VariableValue < IEnumerable\<ciąg >>**  
 **WriteLine**  
 **DelegateArgumentValue\<ciąg >**  
 **Sekwencja**  
 **WriteLine**  
 **Literał\<ciąg >** można pobrać określonego działania zamiast wyliczania wszystkie działania, <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> jest używany. Zarówno <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> i <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> wykonania, jeśli buforowanie metadanych `WorkflowInspectionServices.CacheMetadata` nie została wcześniej wywołana. Jeśli <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> została wywołana następnie <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> opiera się na istniejącą metadanych. W związku z tym jeśli drzewa zostały zmienione od czasu ostatniego wywołania <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> może dać nieoczekiwane wyniki. Jeśli wprowadzono zmiany w przepływie pracy po wywołaniu <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, metadane mogą być buforowane ponownie przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metody. Buforowanie metadanych jest omówiona w następnej sekcji.  
  
### <a name="caching-metadata"></a>Buforowanie metadanych  
 Buforowanie metadanych dla działania kompilacje i weryfikuje opis argumentów działania, zmienne, działania podrzędne i delegatów działania. Metadane, domyślnie jest buforowany przez środowisko uruchomieniowe podczas działania jest gotowa do wykonania. Jeśli autor hosta przepływu pracy chce pamięci podręcznej metadanych dla obiekt activity lub drzewo działań przed tym, na przykład do podejmowania wszelkich kosztów wiedzieli, następnie <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> może służyć do pamięci podręcznej metadanych na żądany czas.
