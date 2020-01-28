---
title: Określanie zainstalowanej wersji platformy WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: 8fc5c380779891b44b7c4f7f8aeb5ed119d8b768
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735695"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="500ed-102">Jak ustalić jaka wersja WPF jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="500ed-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="500ed-103">Numer wersji aktualnie zainstalowanej wersji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znajduje się w **rejestrze**.</span><span class="sxs-lookup"><span data-stu-id="500ed-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="500ed-104">Aby znaleźć numer wersji:</span><span class="sxs-lookup"><span data-stu-id="500ed-104">To find the version number:</span></span>  
  
1. <span data-ttu-id="500ed-105">W menu **Start** kliknij polecenie **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="500ed-105">On the **Start** menu, click **Run**.</span></span>  
  
2. <span data-ttu-id="500ed-106">W obszarze **Otwórz**wpisz **regedit. exe**.</span><span class="sxs-lookup"><span data-stu-id="500ed-106">In **Open**, type **regedit.exe**.</span></span>  
  
3. <span data-ttu-id="500ed-107">Otwórz następujący klucz:</span><span class="sxs-lookup"><span data-stu-id="500ed-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="500ed-108">Numer wersji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest przechowywany w wartości **wersji** .</span><span class="sxs-lookup"><span data-stu-id="500ed-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
