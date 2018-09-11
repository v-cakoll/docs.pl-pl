---
title: Nieprawidłowa wartość sumy kontrolnej, cyfry nieszesnastkowe lub nieparzysta liczba cyfr szesnastkowych
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: e682c2c23dd6fe80aee87d2a86b3df2dae66b802
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276464"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="2a02c-102">Nieprawidłowa wartość sumy kontrolnej, cyfry nieszesnastkowe lub nieparzysta liczba cyfr szesnastkowych</span><span class="sxs-lookup"><span data-stu-id="2a02c-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="2a02c-103">Wartość sumy kontrolnej zawiera nieprawidłowy liczb szesnastkowych lub ma nieparzysta liczba cyfr.</span><span class="sxs-lookup"><span data-stu-id="2a02c-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="2a02c-104">Gdy program ASP.NET wygeneruje plik źródłowy języka Visual Basic (.vb rozszerzenie), oblicza sumy kontrolnej i umieszcza je w pliku źródłowym ukryte identyfikowane przez `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="2a02c-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="2a02c-105">Istnieje możliwość, że użytkownik generowania pliku .vb, w tym również ten proces jest jednak najlepszym od lewej do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="2a02c-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="2a02c-106">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="2a02c-106">By default, this message is a warning.</span></span> <span data-ttu-id="2a02c-107">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2a02c-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2a02c-108">**Identyfikator błędu:** BC42033</span><span class="sxs-lookup"><span data-stu-id="2a02c-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2a02c-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2a02c-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="2a02c-110">Jeśli program ASP.NET generuje plik źródłowy języka Visual Basic, należy ponownie uruchomić kompilacji projektu.</span><span class="sxs-lookup"><span data-stu-id="2a02c-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2.  <span data-ttu-id="2a02c-111">Jeśli to ostrzeżenie będzie nadal występował po ponownym uruchomieniu komputera, ponownej instalacji programu ASP.NET, a następnie ponów próbę kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2a02c-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3.  <span data-ttu-id="2a02c-112">Jeśli to ostrzeżenie będzie nadal występować lub jeśli nie używasz platformy ASP.NET, zebrać informacje dotyczące okoliczności i powiadom pomoc techniczna firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2a02c-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a02c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a02c-113">See also</span></span>

- [<span data-ttu-id="2a02c-114">Omówienie programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2a02c-114">ASP.NET Overview</span></span>](/aspnet/overview)  
- [<span data-ttu-id="2a02c-115">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="2a02c-115">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
