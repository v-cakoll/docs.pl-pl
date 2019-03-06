---
title: 'Instrukcje: Otwórz okno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 9ce7ffb3f46dd869fda7893745b531bd02d18ee1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373572"
---
# <a name="how-to-open-a-window"></a><span data-ttu-id="bdd85-102">Instrukcje: Otwórz okno</span><span class="sxs-lookup"><span data-stu-id="bdd85-102">How to: Open a Window</span></span>
<span data-ttu-id="bdd85-103">Ten przykład przedstawia sposób otworzyć okno.</span><span class="sxs-lookup"><span data-stu-id="bdd85-103">This example shows how to open a window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdd85-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bdd85-104">Example</span></span>  
 <span data-ttu-id="bdd85-105">Okienko jest otwierane przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływać metodę <xref:System.Windows.Window.Show%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bdd85-105">A window is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.Show%2A> method.</span></span> <span data-ttu-id="bdd85-106"><xref:System.Windows.Window.Show%2A> powoduje otwarcie okna i zwraca natychmiast, bez konieczności oczekiwania na nowe okno, aby zamknąć.</span><span class="sxs-lookup"><span data-stu-id="bdd85-106"><xref:System.Windows.Window.Show%2A> opens a window and returns immediately without waiting for the new window to close.</span></span> <span data-ttu-id="bdd85-107">Tym typie okna jest także znana jako *niemodalne* okna, a nie ogranicza dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bdd85-107">This type of window is also known as a *modeless* window, and doesn't restrict user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="bdd85-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bdd85-108">.NET Framework Security</span></span>  
 <span data-ttu-id="bdd85-109">Utworzenie wystąpienia <xref:System.Windows.Window> wymaga uprawnień do wywołania metod natywnych unsafe (zobacz <xref:System.Windows.Window.%23ctor%2A>).</span><span class="sxs-lookup"><span data-stu-id="bdd85-109">Instantiating <xref:System.Windows.Window> requires permission to call unsafe native methods (see <xref:System.Windows.Window.%23ctor%2A>).</span></span>
