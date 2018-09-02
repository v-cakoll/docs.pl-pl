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
ms.openlocfilehash: a1fbbb8415e5e3405f039489aa071b0624065a9d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405894"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="62e69-102">-preferreduilang (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="62e69-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="62e69-103">Za pomocą `-preferreduilang` — opcja kompilatora, można określić język, w którym kompilator języka C#, wyświetla dane wyjściowe, takie jak komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="62e69-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62e69-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="62e69-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="62e69-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="62e69-106">[Nazwa języka](/windows/desktop/Intl/language-names) języka do użycia dla danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="62e69-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62e69-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62e69-107">Remarks</span></span>  
 <span data-ttu-id="62e69-108">Możesz użyć `-preferreduilang` opcję kompilatora, aby określić język, który chcesz, aby kompilator języka C# do użycia dla komunikatów o błędach i inne dane wyjściowe wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="62e69-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="62e69-109">Jeśli nie zainstalowano pakiet językowy dla języka, ustawień języka systemu operacyjnego jest używana zamiast tego, a nie będzie zgłaszany błąd.</span><span class="sxs-lookup"><span data-stu-id="62e69-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="62e69-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62e69-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e69-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62e69-111">See Also</span></span>

- [<span data-ttu-id="62e69-112">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="62e69-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
