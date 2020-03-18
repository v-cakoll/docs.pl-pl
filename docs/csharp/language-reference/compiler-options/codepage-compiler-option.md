---
title: -codepage (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 3352e7fc446ace391540360a3b6b36d604ca5f13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173760"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="99cd5-102">-codepage (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="99cd5-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="99cd5-103">Ta opcja określa, która strona kodowa ma być używana podczas kompilacji, jeśli wymagana strona nie jest bieżącą domyślną stroną kodową systemu.</span><span class="sxs-lookup"><span data-stu-id="99cd5-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99cd5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99cd5-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="99cd5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="99cd5-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="99cd5-106">Identyfikator strony kodowej do użycia dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="99cd5-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99cd5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99cd5-107">Remarks</span></span>  
 <span data-ttu-id="99cd5-108">Kompilator najpierw spróbuje zinterpretować wszystkie pliki źródłowe jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="99cd5-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="99cd5-109">Jeśli pliki kodu źródłowego są w kodowaniu innym niż UTF-8 i używają znaków innych niż 7-bitowe znaki ASCII, użyj opcji **-codepage,** aby określić, która strona kodowa ma być używana.</span><span class="sxs-lookup"><span data-stu-id="99cd5-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="99cd5-110">**-codepage** ma zastosowanie do wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="99cd5-110">**-codepage** applies to all source code files in your compilation.</span></span>  

 <span data-ttu-id="99cd5-111">Zobacz [GetCPInfo,](/windows/desktop/api/winnls/nf-winnls-getcpinfo) aby uzyskać informacje na temat znajdowania stron kodowych, które są obsługiwane w systemie.</span><span class="sxs-lookup"><span data-stu-id="99cd5-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="99cd5-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="99cd5-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cd5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99cd5-113">See also</span></span>

- [<span data-ttu-id="99cd5-114">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="99cd5-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="99cd5-115">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="99cd5-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
