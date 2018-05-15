---
title: -preferreduilang (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 21a3baceb8a46723de1c633e415af0660bb41840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="a2e59-102">-preferreduilang (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a2e59-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="a2e59-103">Za pomocą `-preferreduilang` — opcja kompilatora, można określić język, w którym kompilator języka C# Wyświetla dane wyjściowe, takie jak komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="a2e59-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e59-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2e59-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2e59-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a2e59-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="a2e59-106">[Nazwy języka](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) język do użycia dla danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a2e59-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2e59-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2e59-107">Remarks</span></span>  
 <span data-ttu-id="a2e59-108">Można użyć `-preferreduilang` opcję kompilatora, aby określić język, który ma komunikaty o błędach i innych wiersza polecenia dane wyjściowe kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="a2e59-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="a2e59-109">Jeśli nie zainstalowano pakiet językowy dla języka, zamiast niego jest używana z ustawieniem języka systemu operacyjnego i nie będzie zgłaszany błąd.</span><span class="sxs-lookup"><span data-stu-id="a2e59-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="a2e59-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2e59-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e59-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2e59-111">See Also</span></span>  
 [<span data-ttu-id="a2e59-112">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a2e59-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
