---
title: -codepage (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 59dc1abc3f678a4cf15543c11f9f200ff318ce8f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876928"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="8a36f-102">-codepage (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="8a36f-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="8a36f-103">Ta opcja określa, które stronę kodową do użycia podczas kompilacji, jeśli strona wymagany jest bieżący domyślną stroną kodową systemu.</span><span class="sxs-lookup"><span data-stu-id="8a36f-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a36f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a36f-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="8a36f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8a36f-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="8a36f-106">Identyfikator stronę kodową dla wszystkich plikach kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8a36f-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a36f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a36f-107">Remarks</span></span>  
 <span data-ttu-id="8a36f-108">Kompilator spróbuje najpierw interpretować wszystkie pliki źródłowe w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8a36f-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="8a36f-109">Jeśli pliki kodu źródłowego są w kodowaniu innych niż UTF-8 i używać znaków innych niż 7-bitowe znaki ASCII, użyj **- strona kodowa** opcję, aby określić, stronę kodową, która będzie używana.</span><span class="sxs-lookup"><span data-stu-id="8a36f-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="8a36f-110">**-codepage** ma zastosowanie do wszystkich plikach kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8a36f-110">**-codepage** applies to all source code files in your compilation.</span></span>  
    
 <span data-ttu-id="8a36f-111">Zobacz [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) informacji na temat można znaleźć kodu strony są obsługiwane w systemie.</span><span class="sxs-lookup"><span data-stu-id="8a36f-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="8a36f-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="8a36f-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a36f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a36f-113">See also</span></span>

- [<span data-ttu-id="8a36f-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="8a36f-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="8a36f-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="8a36f-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
