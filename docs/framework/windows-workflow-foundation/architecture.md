---
title: Architektura przepływu pracy systemu Windows
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: c0e21e514e807196f3a09ae2a6eed6a9e7c55a18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="windows-workflow-architecture"></a>Architektura przepływu pracy systemu Windows
Windows Workflow Foundation (WF) podnosi poziom abstrakcji umożliwiający projektowanie aplikacji interaktywnych długotrwałe. Jednostki pracy są hermetyzowane jako działania. Działań uruchamianych w środowisku, które zapewnia ułatwienia sterowanie przepływem, obsługa wyjątków, błędów propagacji trwałości danych o stanie, ładowanie i zwalnianie przepływów pracy w toku z pamięci, śledzenia i przepływu transakcji.  
  
## <a name="activity-architecture"></a>Architektura działania  
 Działania są tworzone jako typów CLR, które pochodzą z dowolnej <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, lub <xref:System.Activities.NativeActivity>, lub ich wariantów, które zwracają wartości, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, lub <xref:System.Activities.NativeActivity%601>. Tworzenie działań, które pochodzą z <xref:System.Activities.Activity> zezwala użytkownikowi na składanie istniejące działania do szybkiego tworzenia jednostek pracy, które są wykonywane w środowisku przepływu pracy. <xref:System.Activities.CodeActivity>, z drugiej strony, umożliwia wykonywanie logiki do maszyny wirtualnej można tworzyć za pomocą kodu zarządzanego <xref:System.Activities.CodeActivityContext> głównie do uzyskiwania dostępu do argumentów działania. <xref:System.Activities.AsyncCodeActivity> przypomina <xref:System.Activities.CodeActivity> z tą różnicą, że może służyć do wykonania zadania asynchronicznego. Tworzenie działań, które pochodzą z <xref:System.Activities.NativeActivity> umożliwia użytkownikom uzyskiwanie dostępu do środowiska uruchomieniowego za pośrednictwem <xref:System.Activities.NativeActivityContext> dla funkcji takich jak zaplanowaniem działań podrzędnych, tworzenia zakładek, wywołania asynchroniczne, rejestrowania transakcji i inne.  
  
 Tworzenie działań, które pochodzą z <xref:System.Activities.Activity> jest deklaratywne i tych działań można tworzyć w języku XAML. W poniższym przykładzie działanie o nazwie `Prompt` jest tworzony przy użyciu innych działań dla treści wykonywania.  
  
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
 <xref:System.Activities.ActivityContext> Jest interfejsem autora działania do środowiska uruchomieniowego przepływu pracy i zapewnia dostęp do środowiska uruchomieniowego wiele funkcji. W poniższym przykładzie działanie zdefiniowano używaną do tworzenia zakładek (mechanizm, który umożliwia działanie, aby zarejestrować punkt kontynuacji można wznowić przez hosta przekazywanie danych do działania na jej wykonanie) kontekstu wykonywania.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Cykl życia działania  
 Wystąpienia działania rozpoczyna się <xref:System.Activities.ActivityInstanceState.Executing> stanu. Jeśli wystąpią wyjątki, pozostaje w tym stanie zakończenie wszystkich działań podrzędnych to wykonywania i inne oczekujące pracy (<xref:System.Activities.Bookmark> obiektów, na przykład) zostało zakończone, w tym momencie przejścia do <xref:System.Activities.ActivityInstanceState.Closed> stanu. Element nadrzędny wystąpienia działania mogą żądać element podrzędny, aby anulować; Jeśli obiekt podrzędny jest w stanie anulować ukończy w <xref:System.Activities.ActivityInstanceState.Canceled> stanu. Jeśli podczas wykonywania jest zgłaszany wyjątek, środowisko uruchomieniowe umieszcza działania do <xref:System.Activities.ActivityInstanceState.Faulted> stanu i propaguje wyjątek zapasowej łańcucha nadrzędnego działań. Stany trzy zakończenia działania są następujące:  
  
-   **Zamknięte:** ukończył pracę i zakończył działanie.  
  
-   **Anulowane:** działanie ma bezpiecznie porzucone jego pracy i zakończony. Praca nie jest jawnie agregowana po wprowadzeniu tego stanu.  
  
-   **Błąd:** działania napotkał błąd i zakończył działanie bez ukończenia pracy.  
  
 Działania pozostają w <xref:System.Activities.ActivityInstanceState.Executing> stanu, gdy są one utrwalona lub zwalnianie modułu.
