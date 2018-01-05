---
title: "BackgroundWorker — Składnik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d83ff69053a71626d0bf9a844d9e94235080d78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="backgroundworker-component"></a><span data-ttu-id="04ac8-102">BackgroundWorker — Składnik</span><span class="sxs-lookup"><span data-stu-id="04ac8-102">BackgroundWorker Component</span></span>
<span data-ttu-id="04ac8-103">`BackgroundWorker` Składnik umożliwia formularz lub formant asynchronicznie uruchom operację.</span><span class="sxs-lookup"><span data-stu-id="04ac8-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04ac8-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="04ac8-104">In This Section</span></span>  
 [<span data-ttu-id="04ac8-105">BackgroundWorker, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="04ac8-105">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="04ac8-106">W tym artykule opisano `BackgroundWorker` składnik, który daje możliwość wykonania czas operacji asynchronicznie ("w tle"), na przez wątek inny niż główny wątek interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04ac8-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="04ac8-107">Przewodnik: przeprowadzanie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="04ac8-107">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="04ac8-108">Pokazuje, jak używać `BackgroundWorker` składnika w projektancie do uruchomienia czasochłonna operacja w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="04ac8-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="04ac8-109">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="04ac8-109">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="04ac8-110">Pokazuje, jak używać `BackgroundWorker` składnik do uruchomienia czasochłonna operacja w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="04ac8-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="04ac8-111">Przewodnik: wdrażanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="04ac8-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="04ac8-112">Tworzy aplikację przy użyciu narzędzia Projektant, który wykonuje obliczenia matematyczne asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="04ac8-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="04ac8-113">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="04ac8-113">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="04ac8-114">Tworzy aplikację, który wykonuje obliczenia matematyczne asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="04ac8-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="04ac8-115">Instrukcje: pobieranie pliku w tle</span><span class="sxs-lookup"><span data-stu-id="04ac8-115">How to: Download a File in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="04ac8-116">Pokazuje, jak używać `BackgroundWorker` składnik można pobrać pliku w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="04ac8-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="04ac8-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="04ac8-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="04ac8-118">Ta klasa opisuje i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="04ac8-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="04ac8-119">Opisuje typ, który przechowuje dane dla <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="04ac8-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="04ac8-120">Opisuje typ, który przechowuje dane dla <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="04ac8-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="04ac8-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="04ac8-121">Related Sections</span></span>  
 [<span data-ttu-id="04ac8-122">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="04ac8-122">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="04ac8-123">W tym artykule opisano, jak wzorca asynchronicznego udostępnia zalety aplikacji wielowątkowych wiele złożonych problemów w wielowątkowe projektu są ukryte.</span><span class="sxs-lookup"><span data-stu-id="04ac8-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
