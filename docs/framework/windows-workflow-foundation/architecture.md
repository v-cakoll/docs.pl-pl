---
title: Architektura przepływu pracy Windows
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: 5d6e1ead9184bfb61eb466389671ca2e74264ae3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723752"
---
# <a name="windows-workflow-architecture"></a>Architektura przepływu pracy Windows
Windows Workflow Foundation (WF) podnosi poziom abstrakcji do tworzenia aplikacji interaktywnych długoterminowych. Jednostki pracy są hermetyzowane jako działania. Działania wykonywane w środowisku, które udostępnia funkcje służące do sterowanie przepływem, obsługa wyjątków, błędów propagacji, trwałości danych o stanie, ładowanie i zwalnianie przepływów pracy w toku, pamięci, śledzenia i przepływu transakcji.  
  
## <a name="activity-architecture"></a>Architektura działania  
 Działania są opracowywane jako typy CLR, które wynikają z poziomu <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.NativeActivity>, lub ich warianty, które zwracają wartość, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, lub <xref:System.Activities.NativeActivity%601>. Tworzenie działań, które wynikają z <xref:System.Activities.Activity> umożliwia użytkownikowi złożyć istniejących działań, aby szybko utworzyć jednostek pracy, które są wykonywane w środowisku przepływu pracy. <xref:System.Activities.CodeActivity>, z drugiej strony, umożliwia wykonywanie logiki można tworzyć przy użyciu kodu zarządzanego <xref:System.Activities.CodeActivityContext> głównie do uzyskiwania dostępu do argumentów działania. <xref:System.Activities.AsyncCodeActivity> jest podobny do <xref:System.Activities.CodeActivity> z tą różnicą, że może służyć do implementowania zadań asynchronicznych. Tworzenie działań, które wynikają z <xref:System.Activities.NativeActivity> pozwala użytkownikom na dostęp w czasie wykonywania za pomocą <xref:System.Activities.NativeActivityContext> dla funkcji, takich jak planowanie dzieci, tworzenia zakładek, wywołanie asynchroniczne, rejestrowanie transakcji i nie tylko.  
  
 Tworzenie działań, które wynikają z <xref:System.Activities.Activity> jest deklaracyjne i te działania można tworzyć w XAML. W poniższym przykładzie działania o nazwie `Prompt` jest tworzony przy użyciu innych działań dla treści wykonywania.  
  
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
 <xref:System.Activities.ActivityContext> Interfejs Autor działania do środowiska wykonawczego przepływów pracy i zapewnia dostęp do środowiska wykonawczego bogactwo funkcji. W poniższym przykładzie zdefiniowano działania, korzystającą z kontekstu wykonania w celu tworzenia zakładki (mechanizm, który umożliwia działanie, aby zarejestrować punkt kontynuacji w jego wykonywania, który może być wznowione przez hosta, przekazując dane do działania).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Cykl życia aktywności  
 Wystąpienie działanie uruchamia w <xref:System.Activities.ActivityInstanceState.Executing> stanu. O ile nie zostaną napotkane wyjątki, pozostaje w tym stanie do momentu wszystkie działania podrzędne zostaną zakończone, wykonywanie i innych oczekujących pracy (<xref:System.Activities.Bookmark> obiektów, na przykład) zostanie zakończone, w tym momencie przejść do <xref:System.Activities.ActivityInstanceState.Closed> stanu. Element nadrzędny wystąpienie działania mogą żądać anulowania; element podrzędny Jeśli element podrzędny jest w stanie zostaną anulowane zostanie ukończone w <xref:System.Activities.ActivityInstanceState.Canceled> stanu. Jeśli wyjątek zostanie zgłoszony podczas wykonywania, środowisko uruchomieniowe przełącza działanie do <xref:System.Activities.ActivityInstanceState.Faulted> stanu i propaguje wyjątek łańcuch nadrzędnego działań. Stany trzy zakończenia działania są następujące:  
  
-   **Zamknięte:** Działanie ukończył pracę i zakończył działanie.  
  
-   **Anulowane:** Działanie ma bez problemu zmieniała porzucone swoją pracę i została zamknięta. Pracy nie jest wycofywany jawnie po wprowadzeniu tego stanu.  
  
-   **Wystąpił błąd:** Działanie napotkał błąd i zakończył działanie bez ukończenia pracy.  
  
 Działania pozostają w <xref:System.Activities.ActivityInstanceState.Executing> stanu, gdy są one utrwalone lub zwolnione.
