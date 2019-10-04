---
title: Architektura programu Windows Workflow
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: e2effc0f53153057b8a9034e4dc80cb19bbe7685
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834867"
---
# <a name="windows-workflow-architecture"></a>Architektura programu Windows Workflow
Windows Workflow Foundation (WF) podnosi poziom abstrakcji na potrzeby tworzenia interaktywnych, długotrwałych aplikacji. Jednostki pracy są hermetyzowane jako działania. Działania działają w środowisku, które zapewnia funkcje kontroli przepływu, obsługi wyjątków, propagacji błędów, trwałości danych stanu, ładowania i zwalniania przepływów pracy w toku z pamięci, śledzenia i przepływu transakcji.  
  
## <a name="activity-architecture"></a>Architektura działań  
 Działania są tworzone jako typy CLR, które pochodzą z <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> lub <xref:System.Activities.NativeActivity> lub ich wariantów, które zwracają wartość, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601> lub <xref:System.Activities.NativeActivity%601>. Opracowywanie działań pochodzących z <xref:System.Activities.Activity> umożliwia użytkownikowi Zgromadzenie istniejących działań w celu szybkiego tworzenia jednostek pracy, które są wykonywane w środowisku przepływu pracy. <xref:System.Activities.CodeActivity>, z drugiej strony, umożliwia tworzenie logiki wykonywania w kodzie zarządzanym przy użyciu <xref:System.Activities.CodeActivityContext> przede wszystkim w celu uzyskania dostępu do argumentów działania. <xref:System.Activities.AsyncCodeActivity> jest podobna do <xref:System.Activities.CodeActivity>, z tą różnicą, że może służyć do implementowania zadań asynchronicznych. Opracowywanie działań pochodzących z <xref:System.Activities.NativeActivity> umożliwia użytkownikom uzyskiwanie dostępu do środowiska uruchomieniowego za pośrednictwem <xref:System.Activities.NativeActivityContext> dla funkcji, takich jak planowanie elementów podrzędnych, tworzenie zakładek, wywoływanie pracy asynchronicznej, rejestrowanie transakcji itd.  
  
 Działania tworzenia, które pochodzą z <xref:System.Activities.Activity>, są deklaratywne i te działania mogą być tworzone w języku XAML. W poniższym przykładzie działanie o nazwie `Prompt` jest tworzone przy użyciu innych działań dla treści wykonania.  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a>Kontekst działania  
 @No__t-0 jest interfejsem autora działania dla środowiska uruchomieniowego przepływu pracy i zapewnia dostęp do bogactwa funkcji środowiska uruchomieniowego. W poniższym przykładzie zdefiniowano działanie, które używa kontekstu wykonywania do utworzenia zakładki (mechanizm, który umożliwia działanie zarejestrowania punktu kontynuacji w jego wykonaniu, który może zostać wznowiony przez hosta przekazującego dane do działania).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Cykl życia aktywności  
 Wystąpienie działania zaczyna się w stanie <xref:System.Activities.ActivityInstanceState.Executing>. O ile nie zostaną napotkane wyjątki, pozostaje w tym stanie do momentu zakończenia wszystkich działań podrzędnych, a każda inna oczekująca praca (<xref:System.Activities.Bookmark> obiektów, na przykład) zostanie zakończona, a następnie przejdzie do stanu <xref:System.Activities.ActivityInstanceState.Closed>. Element nadrzędny wystąpienia działania może zażądać anulowania elementu podrzędnego. Jeśli element podrzędny jest w stanie anulować, kończy się w stanie <xref:System.Activities.ActivityInstanceState.Canceled>. Jeśli wyjątek jest zgłaszany podczas wykonywania, środowisko uruchomieniowe powoduje przełączenie działania do stanu <xref:System.Activities.ActivityInstanceState.Faulted> i propagowanie wyjątku nadrzędnego łańcucha działań. Oto trzy stany ukończenia działania:
  
- **Zamknięte:** Działanie zakończyło pracę i zostało zakończone.  
  
- **Anulowane:** Działanie odrzuciło swoją pracę i zakończyło się. Po wprowadzeniu tego stanu prace nie są jawnie wycofywane z powrotem.  
  
- **Błąd:** Działanie napotkało błąd i zakończyło się bez wykonywania jego pracy.  
  
 Działania pozostają w stanie <xref:System.Activities.ActivityInstanceState.Executing>, gdy zostaną utrwalone lub zwolnione.
