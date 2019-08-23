---
title: -CodePage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 3a5974a910303f847679f18c23e00cfaa00caa2c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962618"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="9ad7d-102">-CodePage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ad7d-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="9ad7d-103">Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9ad7d-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad7d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ad7d-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="9ad7d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9ad7d-105">Arguments</span></span>  
  
|<span data-ttu-id="9ad7d-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9ad7d-106">Term</span></span>|<span data-ttu-id="9ad7d-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9ad7d-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="9ad7d-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="9ad7d-108">Required.</span></span> <span data-ttu-id="9ad7d-109">Kompilator używa strony kodowej określonej przez `id` program, aby interpretować Kodowanie plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="9ad7d-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ad7d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ad7d-110">Remarks</span></span>  
 <span data-ttu-id="9ad7d-111">Aby skompilować kod źródłowy zapisany z określonym kodowaniem, możesz użyć `-codepage` , aby określić, która strona kodowa powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="9ad7d-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="9ad7d-112">`-codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9ad7d-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="9ad7d-113">Aby uzyskać więcej informacji, zobacz [kodowanie znaków w .NET Framework](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="9ad7d-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="9ad7d-114">`-codepage` Opcja nie jest wymagana, jeśli pliki kodu źródłowego zostały zapisane przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 z podpisem.</span><span class="sxs-lookup"><span data-stu-id="9ad7d-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="9ad7d-115">Program Visual Studio zapisuje wszystkie pliki kodu źródłowego z bieżącą stroną kodową ANSI domyślnie, chyba że użytkownik określi inne kodowanie w oknie dialogowym **kodowanie** .</span><span class="sxs-lookup"><span data-stu-id="9ad7d-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="9ad7d-116">Program Visual Studio używa okna dialogowego **kodowanie** do otwierania plików kodu źródłowego zapisanych z inną stroną kodową.</span><span class="sxs-lookup"><span data-stu-id="9ad7d-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ad7d-117">`-codepage` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9ad7d-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad7d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ad7d-118">See also</span></span>

- [<span data-ttu-id="9ad7d-119">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ad7d-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
