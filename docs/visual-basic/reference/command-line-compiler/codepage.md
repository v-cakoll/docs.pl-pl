---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 736b35f51657aa7b21a6a077d70f5e9ff0d4fb85
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="8f422-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f422-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="8f422-103">Określa stronę kodową do użycia dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8f422-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f422-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f422-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f422-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8f422-105">Arguments</span></span>  
  
|<span data-ttu-id="8f422-106">Termin</span><span class="sxs-lookup"><span data-stu-id="8f422-106">Term</span></span>|<span data-ttu-id="8f422-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="8f422-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="8f422-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8f422-108">Required.</span></span> <span data-ttu-id="8f422-109">Kompilator używa strona kodowa określona przez `id` interpretować kodowanie plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="8f422-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f422-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f422-110">Remarks</span></span>  
 <span data-ttu-id="8f422-111">Aby skompilować kod źródłowy został zapisany ze specyficznym kodowaniem, można użyć `-codepage` do określ stronę kodową, która powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="8f422-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="8f422-112">`-codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w sieci kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8f422-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="8f422-113">Aby uzyskać więcej informacji, zobacz [kodowania znaków w programie .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="8f422-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="8f422-114">`-codepage` Opcja nie jest potrzebna, jeśli pliki kodu źródłowego zostały zapisane przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 za pomocą podpisu.</span><span class="sxs-lookup"><span data-stu-id="8f422-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="8f422-115"> zapisuje wszystkie pliki kodu źródłowego z bieżącej strony kodowej ANSI domyślnie, chyba że użytkownik określi inne kodowanie w **kodowanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8f422-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="8f422-116"> używa **kodowanie** okno dialogowe, aby otworzyć zapisane przy użyciu innej strony kodowej plików kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="8f422-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f422-117">`-codepage` Opcja nie jest dostępne w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] środowisko projektowe; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="8f422-117">The `-codepage` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f422-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f422-118">See Also</span></span>  
 [<span data-ttu-id="8f422-119">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f422-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
