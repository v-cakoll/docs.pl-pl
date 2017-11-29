---
title: "Klasa podstawowa działania NativeActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22c9557c53c15fef3ca8dee4a0f665d333c5ffe4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="nativeactivity-base-class"></a>Klasa podstawowa działania NativeActivity
<xref:System.Activities.NativeActivity>jest klasą abstrakcyjną, przy użyciu konstruktora chronionych. Podobnie jak <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> służy do zapisywania konieczne zachowanie zaimplementowanie <xref:System.Activities.NativeActivity.Execute%2A> metody. W odróżnieniu od <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> ma dostęp do wszystkich funkcji dostępnego środowiska uruchomieniowego przepływu pracy za pośrednictwem <xref:System.Activities.NativeActivityContext> obiekt przekazywany do <xref:System.Activities.NativeActivity.Execute%2A> metody.  
  
## <a name="using-nativeactivitycontext"></a>Przy użyciu NativeActivityContext  
 Funkcje środowiska uruchomieniowego przepływu pracy są dostępne z poziomu <xref:System.Activities.NativeActivity.Execute%2A> metody przy użyciu elementów członkowskich `context` parametr typu <xref:System.Activities.NativeActivityContext>. Funkcji dostępnych za pośrednictwem <xref:System.Activities.NativeActivityContext> są następujące:  
  
-   Pobieranie i Ustawianie zmiennych i argumentów.  
  
-   Planowanie działań podrzędnych z<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>  
  
-   Trwa przerywanie wykonywania działania przy użyciu <xref:System.Activities.NativeActivityContext.Abort%2A>.  
  
-   Anulowanie wykonywania podrzędnych za pomocą <xref:System.Activities.NativeActivityContext.CancelChild%2A> i <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.  
  
-   Dostęp do zakładki działania przy użyciu metody, takie jak <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, i <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.  
  
-   Funkcje niestandardowe śledzenia przy użyciu <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   Dostęp do właściwości wykonania działania i wartości właściwości, za pomocą <xref:System.Activities.CodeActivityContext.GetProperty%2A> i <xref:System.Activities.NativeActivityContext.GetValue%2A>.  
  
-   Planowanie działań działania i funkcji przy użyciu <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> i <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>Aby utworzyć niestandardowe działania, który dziedziczy z elementu NativeActivity  
  
1.  Otwórz[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Wybierz **pliku**, **nowe**, a następnie **projektu**. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **Biblioteka działań** w **szablony** okna. Nazwa nowego projektu HelloActivity.  
  
3.  Kliknij prawym przyciskiem myszy Activity1.xaml w projekcie HelloActivity i wybierz **usunąć**.  
  
4.  Kliknij prawym przyciskiem myszy projekt HelloActivity i wybierz **Dodaj**, a następnie **klasy**. Nazwa nowej klasy HelloActivity.cs.  
  
5.  W pliku HelloActivity.cs, Dodaj następujący `using` dyrektywy.  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Upewnij się nowa klasa dziedziczy <xref:System.Activities.NativeActivity> przez dodanie klasy podstawowej deklaracji klasy.  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  Dodawanie funkcji do klasy, dodając <xref:System.Activities.NativeActivity.Execute%2A> metody.  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Zastąpienie <xref:System.Activities.NativeActivity.CacheMetadata%2A> — metoda i wywołanie odpowiedniej metody Add, aby umożliwić wiedzieć o działań niestandardowych zmiennych, argumenty elementów podrzędnych i delegatów środowiska uruchomieniowego przepływu pracy. Aby uzyskać więcej informacji, zobacz <xref:System.Activities.NativeActivityMetadata> klasy.  
  
9. Użyj <xref:System.Activities.NativeActivityContext> obiektu można zaplanować zakładki. Zobacz <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> szczegółowe informacje dotyczące sposobu tworzenia, planowanie i wznowić zakładki.  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
