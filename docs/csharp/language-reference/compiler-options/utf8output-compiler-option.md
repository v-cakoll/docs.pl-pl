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
ms.openlocfilehash: 32c239f7563101cb1dddedbf868d298806353492
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43476264"
---
# <a name="-utf8output-c-compiler-options"></a><span data-ttu-id="d96f6-102">-utf8output (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d96f6-102">-utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="d96f6-103">**-Utf8output** opcji powoduje wyświetlenie kompilatora, dane wyjściowe przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d96f6-103">The **-utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d96f6-104">Syntax</span></span>  
  
```console  
-utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="d96f6-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d96f6-105">Remarks</span></span>  
 <span data-ttu-id="d96f6-106">W niektórych konfiguracjach międzynarodowe dane wyjściowe kompilatora poprawnie nie można wyświetlić w konsoli.</span><span class="sxs-lookup"><span data-stu-id="d96f6-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="d96f6-107">W tych konfiguracjach, należy użyć **-utf8output** i przekierować dane wyjściowe kompilatora do pliku.</span><span class="sxs-lookup"><span data-stu-id="d96f6-107">In these configurations, use **-utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="d96f6-108">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="d96f6-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96f6-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d96f6-109">See Also</span></span>  

- [<span data-ttu-id="d96f6-110">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d96f6-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
