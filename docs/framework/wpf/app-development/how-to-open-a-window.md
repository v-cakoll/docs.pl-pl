---
title: 'Porady: otwieranie okna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 23dc74666d8f47a0fb735d96ad22ed56c96bdbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-open-a-window"></a><span data-ttu-id="a10e1-102">Porady: otwieranie okna</span><span class="sxs-lookup"><span data-stu-id="a10e1-102">How to: Open a Window</span></span>
<span data-ttu-id="a10e1-103">Ten przykład przedstawia sposób otwierania okna.</span><span class="sxs-lookup"><span data-stu-id="a10e1-103">This example shows how to open a window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a10e1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a10e1-104">Example</span></span>  
 <span data-ttu-id="a10e1-105">Okno jest otwarty przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływania <xref:System.Windows.Window.Show%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a10e1-105">A window is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.Show%2A> method.</span></span> <span data-ttu-id="a10e1-106"><xref:System.Windows.Window.Show%2A> Otwiera okno i zwraca natychmiast bez oczekiwania na nowe okno, aby zamknąć.</span><span class="sxs-lookup"><span data-stu-id="a10e1-106"><xref:System.Windows.Window.Show%2A> opens a window and returns immediately without waiting for the new window to close.</span></span> <span data-ttu-id="a10e1-107">Okno tego typu jest nazywana *niemodalne* okna i nie stanowi ograniczenia danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a10e1-107">This type of window is also known as a *modeless* window, and doesn't restrict user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="a10e1-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a10e1-108">.NET Framework Security</span></span>  
 <span data-ttu-id="a10e1-109">Tworzenie wystąpień <xref:System.Windows.Window> wymaga uprawnienia do wywoływania metod natywnych unsafe (zobacz <xref:System.Windows.Window.%23ctor%2A>).</span><span class="sxs-lookup"><span data-stu-id="a10e1-109">Instantiating <xref:System.Windows.Window> requires permission to call unsafe native methods (see <xref:System.Windows.Window.%23ctor%2A>).</span></span>
