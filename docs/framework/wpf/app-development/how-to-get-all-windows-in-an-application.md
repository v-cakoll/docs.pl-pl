---
title: 'Instrukcje: Pobieranie wszystkich okien w aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947774"
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="0da5a-102">Instrukcje: Pobieranie wszystkich okien w aplikacji</span><span class="sxs-lookup"><span data-stu-id="0da5a-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="0da5a-103">W tym przykładzie pokazano, jak pobrać wszystkie <xref:System.Windows.Window> obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0da5a-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0da5a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0da5a-104">Example</span></span>  
 <span data-ttu-id="0da5a-105">Każdego wystąpienia <xref:System.Windows.Window> obiektu, czy jest widoczny lub nie jest automatycznie dodawany do kolekcji odwołań do okna, które jest zarządzane przez <xref:System.Windows.Application>i narażonych z <xref:System.Windows.Application.Windows%2A>.</span><span class="sxs-lookup"><span data-stu-id="0da5a-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="0da5a-106">Można wyliczyć <xref:System.Windows.Application.Windows%2A> można pobrać wszystkich wystąpień systemu windows, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="0da5a-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
