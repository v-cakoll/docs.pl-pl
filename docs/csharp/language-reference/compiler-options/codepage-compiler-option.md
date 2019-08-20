---
title: -CodePage (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: c85cd8935bcefd1353707624052b62ee982f7b07
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603053"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="95c4d-102">-CodePage (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="95c4d-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="95c4d-103">Ta opcja określa, która strona kodowa ma być używana podczas kompilacji, jeśli wymagana Strona nie jest bieżącą domyślną stroną kodową systemu.</span><span class="sxs-lookup"><span data-stu-id="95c4d-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c4d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95c4d-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="95c4d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="95c4d-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="95c4d-106">Identyfikator strony kodowej, który ma być używany dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="95c4d-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95c4d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95c4d-107">Remarks</span></span>  
 <span data-ttu-id="95c4d-108">Kompilator spróbuje najpierw zinterpretować wszystkie pliki źródłowe jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="95c4d-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="95c4d-109">Jeśli pliki kodu źródłowego są w kodowaniu innym niż UTF-8 i są używane znaki inne niż 7-bitowe znaki ASCII, użyj opcji **-CodePage** , aby określić, która strona kodowa powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="95c4d-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="95c4d-110">**-CodePage** stosuje się do wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="95c4d-110">**-codepage** applies to all source code files in your compilation.</span></span>  
    
 <span data-ttu-id="95c4d-111">Zobacz [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) , aby uzyskać informacje na temat sposobu znajdowania, które strony kodowe są obsługiwane w systemie.</span><span class="sxs-lookup"><span data-stu-id="95c4d-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="95c4d-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="95c4d-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c4d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95c4d-113">See also</span></span>

- [<span data-ttu-id="95c4d-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="95c4d-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="95c4d-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="95c4d-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
