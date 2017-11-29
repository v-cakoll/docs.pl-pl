---
title: -utf8output (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /utf8output
helpviewer_keywords:
- utf8output compiler option [C#]
- /utf8output compiler option [C#]
- -utf8output compiler option [C#]
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 95630afcfcd2ae9ab64660eb0f022dd0733b4c4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="utf8output-c-compiler-options"></a><span data-ttu-id="facfa-102">/utf8output (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="facfa-102">/utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="facfa-103">**/Utf8output** opcja powoduje wyświetlenie kompilatora, dane wyjściowe przy użyciu kodowania UTF-8.</span><span class="sxs-lookup"><span data-stu-id="facfa-103">The **/utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facfa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="facfa-104">Syntax</span></span>  
  
```console  
/utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="facfa-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="facfa-105">Remarks</span></span>  
 <span data-ttu-id="facfa-106">W niektórych konfiguracjach międzynarodowe dane wyjściowe kompilatora poprawnie nie można wyświetlić w konsoli.</span><span class="sxs-lookup"><span data-stu-id="facfa-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="facfa-107">W tych konfiguracjach, użyj **/utf8output** i Przekieruj dane wyjściowe kompilatora do pliku.</span><span class="sxs-lookup"><span data-stu-id="facfa-107">In these configurations, use **/utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="facfa-108">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="facfa-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facfa-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="facfa-109">See Also</span></span>  
 [<span data-ttu-id="facfa-110">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="facfa-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
