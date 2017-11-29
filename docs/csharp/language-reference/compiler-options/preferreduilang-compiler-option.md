---
title: -preferreduilang (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ccf25e9a5d5d025f9024519b41c4afa17a5081f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="preferreduilang-c-compiler-options"></a><span data-ttu-id="46212-102">/preferreduilang (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="46212-102">/preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="46212-103">Za pomocą `/preferreduilang` — opcja kompilatora, można określić język, w którym kompilator języka C# Wyświetla dane wyjściowe, takie jak komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="46212-103">By using the `/preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46212-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46212-104">Syntax</span></span>  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="46212-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="46212-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="46212-106">[Nazwy języka](http://go.microsoft.com/fwlink/p/?LinkId=236992) język do użycia dla danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="46212-106">The [language name](http://go.microsoft.com/fwlink/p/?LinkId=236992) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46212-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46212-107">Remarks</span></span>  
 <span data-ttu-id="46212-108">Można użyć `/preferreduilang` opcję kompilatora, aby określić język, który ma komunikaty o błędach i innych wiersza polecenia dane wyjściowe kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="46212-108">You can use the `/preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="46212-109">Jeśli nie zainstalowano pakiet językowy dla języka, zamiast niego jest używana z ustawieniem języka systemu operacyjnego i nie będzie zgłaszany błąd.</span><span class="sxs-lookup"><span data-stu-id="46212-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="46212-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46212-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46212-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46212-111">See Also</span></span>  
 [<span data-ttu-id="46212-112">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="46212-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
