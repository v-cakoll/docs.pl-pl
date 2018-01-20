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
ms.openlocfilehash: 4fcf075dd951d733d294a62de98365c77b16a51d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="e7bf2-102">-preferreduilang (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="e7bf2-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="e7bf2-103">Za pomocą `-preferreduilang` — opcja kompilatora, można określić język, w którym kompilator języka C# Wyświetla dane wyjściowe, takie jak komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="e7bf2-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7bf2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7bf2-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7bf2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e7bf2-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="e7bf2-106">[Nazwy języka](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) język do użycia dla danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e7bf2-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7bf2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7bf2-107">Remarks</span></span>  
 <span data-ttu-id="e7bf2-108">Można użyć `-preferreduilang` opcję kompilatora, aby określić język, który ma komunikaty o błędach i innych wiersza polecenia dane wyjściowe kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="e7bf2-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="e7bf2-109">Jeśli nie zainstalowano pakiet językowy dla języka, zamiast niego jest używana z ustawieniem języka systemu operacyjnego i nie będzie zgłaszany błąd.</span><span class="sxs-lookup"><span data-stu-id="e7bf2-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="e7bf2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7bf2-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bf2-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7bf2-111">See Also</span></span>  
 [<span data-ttu-id="e7bf2-112">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="e7bf2-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
