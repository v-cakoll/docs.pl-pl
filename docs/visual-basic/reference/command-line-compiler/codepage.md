---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 34dbf36cc79a8c4715cf6a07c57d559e14f40030
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363633"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="bbfc9-102">-CodePage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbfc9-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="bbfc9-103">Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bbfc9-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbfc9-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="bbfc9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bbfc9-105">Arguments</span></span>  
  
|<span data-ttu-id="bbfc9-106">Termin</span><span class="sxs-lookup"><span data-stu-id="bbfc9-106">Term</span></span>|<span data-ttu-id="bbfc9-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="bbfc9-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="bbfc9-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="bbfc9-108">Required.</span></span> <span data-ttu-id="bbfc9-109">Kompilator używa strony kodowej określonej przez program, `id` Aby interpretować Kodowanie plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="bbfc9-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbfc9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbfc9-110">Remarks</span></span>  
 <span data-ttu-id="bbfc9-111">Aby skompilować kod źródłowy zapisany z określonym kodowaniem, możesz użyć, `-codepage` Aby określić, która strona kodowa powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="bbfc9-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="bbfc9-112">`-codepage`Opcja ma zastosowanie do wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bbfc9-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="bbfc9-113">Aby uzyskać więcej informacji, zobacz [kodowanie znaków w .NET Framework](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="bbfc9-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="bbfc9-114">`-codepage`Opcja nie jest wymagana, jeśli pliki kodu źródłowego zostały zapisane przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 z podpisem.</span><span class="sxs-lookup"><span data-stu-id="bbfc9-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="bbfc9-115">Program Visual Studio zapisuje wszystkie pliki kodu źródłowego z bieżącą stroną kodową ANSI domyślnie, chyba że użytkownik określi inne kodowanie w oknie dialogowym **kodowanie** .</span><span class="sxs-lookup"><span data-stu-id="bbfc9-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="bbfc9-116">Program Visual Studio używa okna dialogowego **kodowanie** do otwierania plików kodu źródłowego zapisanych z inną stroną kodową.</span><span class="sxs-lookup"><span data-stu-id="bbfc9-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbfc9-117">`-codepage`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bbfc9-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfc9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbfc9-118">See also</span></span>

- [<span data-ttu-id="bbfc9-119">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bbfc9-119">Visual Basic Command-Line Compiler</span></span>](index.md)
