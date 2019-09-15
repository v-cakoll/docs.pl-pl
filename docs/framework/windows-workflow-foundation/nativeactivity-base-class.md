---
title: NativeActivity, klasa bazowa
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 604535e39937a75c6d268cf1abbc90dbcd506a16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989552"
---
# <a name="nativeactivity-base-class"></a>NativeActivity, klasa bazowa

<xref:System.Activities.NativeActivity>jest klasą abstrakcyjną z chronionym konstruktorem. Na przykład, <xref:System.Activities.NativeActivity> jest używany do pisania bezwzględnego zachowania <xref:System.Activities.NativeActivity.Execute%2A> przez implementację metody. <xref:System.Activities.CodeActivity> W <xref:System.Activities.CodeActivity>przeciwieństwie <xref:System.Activities.NativeActivity> do, ma dostęp do wszystkich narażonych funkcji środowiska uruchomieniowego przepływu pracy <xref:System.Activities.NativeActivityContext> za pomocą obiektu przesłanego do <xref:System.Activities.NativeActivity.Execute%2A> metody.

## <a name="using-nativeactivitycontext"></a>Korzystanie z NativeActivityContext
 Dostęp do funkcji środowiska uruchomieniowego przepływu pracy można uzyskać z <xref:System.Activities.NativeActivity.Execute%2A> poziomu metody przy użyciu elementów członkowskich `context` parametru typu <xref:System.Activities.NativeActivityContext>. Dostępne <xref:System.Activities.NativeActivityContext> są następujące funkcje:

- Pobieranie i określanie argumentów i zmiennych.

- Planowanie działań podrzędnych przy użyciu<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>

- Przerywanie wykonywania działania przy <xref:System.Activities.NativeActivityContext.Abort%2A>użyciu.

- Anulowanie wykonywania elementu podrzędnego <xref:System.Activities.NativeActivityContext.CancelChild%2A> za <xref:System.Activities.NativeActivityContext.CancelChildren%2A>pomocą i.

- Dostęp do zakładek aktywności przy użyciu takich <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>metod <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>jak, <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>i.

- Niestandardowe funkcje śledzenia przy <xref:System.Activities.CodeActivityContext.Track%2A>użyciu programu.

- Dostęp do właściwości wykonywania działania i właściwości wartości przy użyciu <xref:System.Activities.CodeActivityContext.GetProperty%2A> i. <xref:System.Activities.NativeActivityContext.GetValue%2A>

- Planowanie akcji i funkcji działania przy <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> użyciu <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>i.

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>Aby utworzyć niestandardowe działanie, które dziedziczy z natywnego

1. OpenVisual Studio 2010.

2. Wybierz kolejno opcje **plik**, **Nowy**i **projekt**. Wybierz pozycję **Workflow 4,0** w obszarze **Wizualizacja C#**  w oknie **typy projektów** , a następnie wybierz węzeł **V2010** . Wybierz pozycję **Biblioteka działań** w oknie **Szablony** . Nadaj nazwę nowej powitaniu projektu.

3. Kliknij prawym przyciskiem myszy pozycję zakończeniu. XAML w projekcie Hello i wybierz polecenie **Usuń**.

4. Kliknij prawym przyciskiem myszy projekt Hello i wybierz polecenie **Dodaj**, a następnie **klasy**. Nadaj nowej klasie nazwę HelloActivity.cs.

5. W pliku HelloActivity.cs Dodaj następujące `using` dyrektywy.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. Uczyń nową klasę dziedziczą <xref:System.Activities.NativeActivity> przez dodanie klasy bazowej do deklaracji klasy.

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. Dodaj funkcję do klasy, <xref:System.Activities.NativeActivity.Execute%2A> dodając metodę.

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. Zastąp <xref:System.Activities.NativeActivity.CacheMetadata%2A> metodę i Wywołaj odpowiednią metodę Add, aby umożliwić środowisko uruchomieniowe przepływu pracy znać zmienne, argumenty, elementy podrzędne i Delegaty działania niestandardowego. Aby uzyskać więcej informacji, <xref:System.Activities.NativeActivityMetadata> zobacz Klasa.

9. Użyj obiektu <xref:System.Activities.NativeActivityContext> , aby zaplanować zakładkę. Zobacz <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> , aby uzyskać szczegółowe informacje na temat tworzenia, planowania i wznawiania zakładki.

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
