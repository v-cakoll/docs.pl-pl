---
title: /codepage (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 609373ed0e58eec86a703f33d48d31e27b0b7e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="codepage-visual-basic"></a><span data-ttu-id="941b1-102">/codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="941b1-102">/codepage (Visual Basic)</span></span>
<span data-ttu-id="941b1-103">Określa stronę kodową do użycia dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="941b1-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="941b1-104">Syntax</span></span>  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="941b1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="941b1-105">Arguments</span></span>  
  
|<span data-ttu-id="941b1-106">Termin</span><span class="sxs-lookup"><span data-stu-id="941b1-106">Term</span></span>|<span data-ttu-id="941b1-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="941b1-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="941b1-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="941b1-108">Required.</span></span> <span data-ttu-id="941b1-109">Kompilator używa strona kodowa określona przez `id` interpretować kodowanie plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="941b1-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="941b1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="941b1-110">Remarks</span></span>  
 <span data-ttu-id="941b1-111">Aby skompilować kod źródłowy został zapisany ze specyficznym kodowaniem, można użyć `/codepage` do określ stronę kodową, która powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="941b1-111">To compile source code saved with a specific encoding, you can use `/codepage` to specify which code page should be used.</span></span> <span data-ttu-id="941b1-112">`/codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w sieci kompilacji.</span><span class="sxs-lookup"><span data-stu-id="941b1-112">The `/codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="941b1-113">Aby uzyskać więcej informacji, zobacz [kodowania znaków w programie .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="941b1-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="941b1-114">`/codepage` Opcja nie jest potrzebna, jeśli pliki kodu źródłowego zostały zapisane przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 za pomocą podpisu.</span><span class="sxs-lookup"><span data-stu-id="941b1-114">The `/codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="941b1-115">zapisuje wszystkie pliki kodu źródłowego z bieżącej strony kodowej ANSI domyślnie, chyba że użytkownik określi inne kodowanie w **kodowanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="941b1-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="941b1-116">używa **kodowanie** okno dialogowe, aby otworzyć zapisane przy użyciu innej strony kodowej plików kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="941b1-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="941b1-117">`/codepage` Opcja nie jest dostępne w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] środowisko projektowe; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="941b1-117">The `/codepage` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941b1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="941b1-118">See Also</span></span>  
 [<span data-ttu-id="941b1-119">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="941b1-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
