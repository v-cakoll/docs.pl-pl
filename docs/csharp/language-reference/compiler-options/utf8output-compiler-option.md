---
title: -utf8output (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /utf8output
helpviewer_keywords:
- utf8output compiler option [C#]
- /utf8output compiler option [C#]
- -utf8output compiler option [C#]
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
ms.openlocfilehash: 9dd67d3ea14b02ae9638f3b13d6bca0a84e4b71b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691518"
---
# <a name="-utf8output-c-compiler-options"></a><span data-ttu-id="26989-102">-utf8output (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="26989-102">-utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="26989-103">**-Utf8output** opcji powoduje wyświetlenie kompilatora, dane wyjściowe przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="26989-103">The **-utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26989-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26989-104">Syntax</span></span>  
  
```console  
-utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="26989-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26989-105">Remarks</span></span>  
 <span data-ttu-id="26989-106">W niektórych konfiguracjach międzynarodowe dane wyjściowe kompilatora poprawnie nie można wyświetlić w konsoli.</span><span class="sxs-lookup"><span data-stu-id="26989-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="26989-107">W tych konfiguracjach, należy użyć **-utf8output** i przekierować dane wyjściowe kompilatora do pliku.</span><span class="sxs-lookup"><span data-stu-id="26989-107">In these configurations, use **-utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="26989-108">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="26989-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26989-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26989-109">See also</span></span>

- [<span data-ttu-id="26989-110">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="26989-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
