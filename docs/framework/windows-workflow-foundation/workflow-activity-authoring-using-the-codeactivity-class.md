---
title: Tworzenie działań przepływu pracy przy użyciu klasy CodeActivity
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 549acec8b8101312d48bd20e63a4a988b798ff38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767399"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>Tworzenie działań przepływu pracy przy użyciu klasy CodeActivity
Działania utworzone przez dziedziczenie z <xref:System.Activities.CodeActivity> można zaimplementować podstawowe zachowanie imperatywne przez zastąpienie <xref:System.Activities.CodeActivity.Execute%2A> metody.

## <a name="using-codeactivitycontext"></a>Za pomocą CodeActivityContext
 Funkcje środowiska wykonawczego przepływów pracy są dostępne z poziomu <xref:System.Activities.CodeActivity.Execute%2A> metody za pomocą elementów członkowskich `context` parametr typu <xref:System.Activities.CodeActivityContext>. Funkcje dostępne za pośrednictwem <xref:System.Activities.CodeActivityContext> obejmują następujące elementy:

-   Pobieranie i ustawianie wartości zmiennych i argumentów.

-   Niestandardowe śledzenia funkcji przy użyciu <xref:System.Activities.CodeActivityContext.Track%2A>.

-   Dostęp do właściwości wykonania działania przy użyciu <xref:System.Activities.CodeActivityContext.GetProperty%2A>.

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>Aby utworzyć niestandardowe działanie, która dziedziczy z elementu CodeActivity

1. Open Visual Studio 2010.

2. Wybierz **pliku**, **nowe**, a następnie **projektu**. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **Biblioteka działań** w **szablony** okna. Nazwa nowego projektu HelloActivity.

3. Kliknij prawym przyciskiem myszy Activity1.xaml w projekcie HelloActivity, a następnie wybierz pozycję **Usuń**.

4. Kliknij prawym przyciskiem myszy projekt HelloActivity, a następnie wybierz pozycję **Dodaj** , a następnie **klasy**. Nazwa nowej klasy HelloActivity.cs.

5. W pliku HelloActivity.cs, Dodaj następujący kod `using` dyrektywy.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. Wprowadź nowy dziedziczyć z klasy <xref:System.Activities.CodeActivity> przez dodanie klasy bazowej do deklaracji klasy.

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. Dodawanie funkcji do klasy, dodając <xref:System.Activities.CodeActivity.Execute%2A> metody.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. Użyj <xref:System.Activities.CodeActivityContext> do tworzenia rekordów śledzenia.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
