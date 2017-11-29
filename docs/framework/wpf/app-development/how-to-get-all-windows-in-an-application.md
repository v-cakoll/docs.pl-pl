---
title: 'Porady: uzyskiwanie wszystkich okien aplikacji'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8577817f62ece1465f9c7577f3e1b7ff5ecefe44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="9752c-102">Porady: uzyskiwanie wszystkich okien aplikacji</span><span class="sxs-lookup"><span data-stu-id="9752c-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="9752c-103">W tym przykładzie pokazano, jak pobrać wszystkie <xref:System.Windows.Window> obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9752c-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9752c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9752c-104">Example</span></span>  
 <span data-ttu-id="9752c-105">Co wystąpienia <xref:System.Windows.Window> obiektu, czy jest widoczny czy nie, zostanie automatycznie dodany do kolekcji odwołań do okna, które jest zarządzane przez <xref:System.Windows.Application>i narażonych z <xref:System.Windows.Application.Windows%2A>.</span><span class="sxs-lookup"><span data-stu-id="9752c-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="9752c-106">Można wyliczyć <xref:System.Windows.Application.Windows%2A> można pobrać wszystkich wystąpień systemu windows, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9752c-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
