---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: fda75383435fdff718d1d50bc8583afc9858e7e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944706"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="9805a-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9805a-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="9805a-103">Określa stronę kodową dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9805a-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9805a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9805a-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="9805a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9805a-105">Arguments</span></span>  
  
|<span data-ttu-id="9805a-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9805a-106">Term</span></span>|<span data-ttu-id="9805a-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9805a-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="9805a-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9805a-108">Required.</span></span> <span data-ttu-id="9805a-109">Kompilator używa strony kodowej, określony przez `id` interpretowanie kodowanie plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="9805a-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9805a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9805a-110">Remarks</span></span>  
 <span data-ttu-id="9805a-111">Aby skompilować kod źródłowy został zapisany ze specyficznym kodowaniem, można użyć `-codepage` można określić stronę kodową, która będzie używana.</span><span class="sxs-lookup"><span data-stu-id="9805a-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="9805a-112">`-codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9805a-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="9805a-113">Aby uzyskać więcej informacji, zobacz [kodowanie znaków na platformie .NET Framework](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="9805a-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="9805a-114">`-codepage` Opcja nie jest potrzebna, jeśli zostały zapisane pliki kodu źródłowego, przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 z podpisem.</span><span class="sxs-lookup"><span data-stu-id="9805a-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="9805a-115">Program Visual Studio zapisuje wszystkie pliki kodu źródłowego za pomocą bieżącej strony kodowej ANSI domyślnie, chyba że użytkownik określi, inne kodowanie w **kodowanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="9805a-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="9805a-116">Program Visual Studio używa **kodowanie** okno dialogowe Otwieranie plików kodu źródłowego, zapisany z inną stronę kodową.</span><span class="sxs-lookup"><span data-stu-id="9805a-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9805a-117">`-codepage` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="9805a-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9805a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9805a-118">See also</span></span>

- [<span data-ttu-id="9805a-119">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9805a-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
