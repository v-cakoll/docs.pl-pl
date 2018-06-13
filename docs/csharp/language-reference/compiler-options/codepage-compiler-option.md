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
ms.openlocfilehash: 04a0d3a62ebd2b3a938445995725994d72d5bd4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216928"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="9c4e1-102">-codepage (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="9c4e1-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="9c4e1-103">Ta opcja określa, które stronę kodową do używania podczas kompilacji, jeśli wymagane strony nie jest bieżącym domyślna strona kodowa systemu.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c4e1-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="9c4e1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9c4e1-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="9c4e1-106">Identyfikator strony kodowej do użycia dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c4e1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c4e1-107">Remarks</span></span>  
 <span data-ttu-id="9c4e1-108">Jeśli kompilacja jeden lub więcej plików kodu źródłowego, które nie zostały utworzone do użycia na domyślną stronę kodową na komputerze, możesz użyć **- codepage** opcję, aby określić stronę kodową, która będzie używana.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="9c4e1-109">**-codepage** ma zastosowanie do wszystkich plików kodu źródłowego w sieci kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="9c4e1-110">Jeśli zostały utworzone pliki kodu źródłowego za pomocą tego samego stronę kodową, która działa na komputerze lub jeśli pliki kodu źródłowego zostały utworzone z UNICODE lub UTF-8, należy stosować **- codepage**.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="9c4e1-111">Zobacz [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) informacji na temat znajdowania które kodu strony są obsługiwane w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-111">See [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="9c4e1-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4e1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c4e1-113">See Also</span></span>  
 [<span data-ttu-id="9c4e1-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="9c4e1-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="9c4e1-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="9c4e1-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
