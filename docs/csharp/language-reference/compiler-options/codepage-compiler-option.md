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
ms.openlocfilehash: 66edb32d24dd1dc543097b98ff3744f0aa0a7145
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511875"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="38cd3-102">-codepage (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="38cd3-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="38cd3-103">Ta opcja określa, które stronę kodową do użycia podczas kompilacji, jeśli strona wymagany jest bieżący domyślną stroną kodową systemu.</span><span class="sxs-lookup"><span data-stu-id="38cd3-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38cd3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38cd3-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="38cd3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="38cd3-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="38cd3-106">Identyfikator stronę kodową dla wszystkich plikach kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="38cd3-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38cd3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38cd3-107">Remarks</span></span>  
 <span data-ttu-id="38cd3-108">Jeśli kompilujesz jeden lub więcej plików kodu źródłowego, które nie zostały utworzone do użycia z domyślną stroną kodową na komputerze, możesz użyć **- strona kodowa** opcję, aby określić, stronę kodową, która będzie używana.</span><span class="sxs-lookup"><span data-stu-id="38cd3-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="38cd3-109">**-codepage** ma zastosowanie do wszystkich plikach kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="38cd3-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="38cd3-110">Jeśli pliki kodu źródłowego zostały utworzone za pomocą tej samej strony kodowej, która działa na komputerze lub w plikach kodu źródłowego zostały utworzone przy użyciu standardu UNICODE lub UTF-8, należy stosować **- strona kodowa**.</span><span class="sxs-lookup"><span data-stu-id="38cd3-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="38cd3-111">Zobacz [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) informacji na temat można znaleźć kodu strony są obsługiwane w systemie.</span><span class="sxs-lookup"><span data-stu-id="38cd3-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="38cd3-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="38cd3-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38cd3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38cd3-113">See Also</span></span>  

- [<span data-ttu-id="38cd3-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="38cd3-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="38cd3-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="38cd3-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
