---
title: Jak ustalić jaka wersja WPF jest zainstalowana
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: c59fa0d0a4d94c6e6a2ab72a4cd7a3c066649fb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="ebfaf-102">Jak ustalić jaka wersja WPF jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="ebfaf-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="ebfaf-103">Numer wersji dla bieżącej wersji zainstalowanego [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znajduje się w **rejestru**.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="ebfaf-104">Aby określić numer wersji:</span><span class="sxs-lookup"><span data-stu-id="ebfaf-104">To find the version number:</span></span>  
  
1.  <span data-ttu-id="ebfaf-105">Na **Start** menu, kliknij przycisk **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="ebfaf-106">W **Otwórz**, typ **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-106">In **Open**, type **regedit.exe**.</span></span>  
  
3.  <span data-ttu-id="ebfaf-107">Otwórz następujący klucz:</span><span class="sxs-lookup"><span data-stu-id="ebfaf-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="ebfaf-108">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Numer wersji jest zapisany w **wersji** wartość.</span><span class="sxs-lookup"><span data-stu-id="ebfaf-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
