---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 8aee51df3ba9f92ca662fbbfbd73998e4a3b4538
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532513"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="92add-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92add-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="92add-103">Określa stronę kodową dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="92add-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92add-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92add-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="92add-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="92add-105">Arguments</span></span>  
  
|<span data-ttu-id="92add-106">Termin</span><span class="sxs-lookup"><span data-stu-id="92add-106">Term</span></span>|<span data-ttu-id="92add-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="92add-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="92add-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="92add-108">Required.</span></span> <span data-ttu-id="92add-109">Kompilator używa strony kodowej, określony przez `id` interpretowanie kodowanie plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="92add-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92add-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92add-110">Remarks</span></span>  
 <span data-ttu-id="92add-111">Aby skompilować kod źródłowy został zapisany ze specyficznym kodowaniem, można użyć `-codepage` można określić stronę kodową, która będzie używana.</span><span class="sxs-lookup"><span data-stu-id="92add-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="92add-112">`-codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="92add-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="92add-113">Aby uzyskać więcej informacji, zobacz [kodowanie znaków na platformie .NET Framework](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="92add-113">For more information, see [Character Encoding in the .NET Framework](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="92add-114">`-codepage` Opcja nie jest potrzebna, jeśli zostały zapisane pliki kodu źródłowego, przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 z podpisem.</span><span class="sxs-lookup"><span data-stu-id="92add-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="92add-115">Program Visual Studio zapisuje wszystkie pliki kodu źródłowego za pomocą bieżącej strony kodowej ANSI domyślnie, chyba że użytkownik określi, inne kodowanie w **kodowanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="92add-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="92add-116">Program Visual Studio używa **kodowanie** okno dialogowe Otwieranie plików kodu źródłowego, zapisany z inną stronę kodową.</span><span class="sxs-lookup"><span data-stu-id="92add-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92add-117">`-codepage` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="92add-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92add-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92add-118">See Also</span></span>  
 [<span data-ttu-id="92add-119">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92add-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
