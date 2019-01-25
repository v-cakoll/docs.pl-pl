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
ms.openlocfilehash: d079441e91ff90bcc974564bbd7069e0548a7d77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575300"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="28e09-102">-preferreduilang (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="28e09-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="28e09-103">Za pomocą `-preferreduilang` — opcja kompilatora, można określić język, w którym kompilator języka C#, wyświetla dane wyjściowe, takie jak komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="28e09-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28e09-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="28e09-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="28e09-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="28e09-106">[Nazwa języka](/windows/desktop/Intl/language-names) języka do użycia dla danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="28e09-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28e09-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28e09-107">Remarks</span></span>  
 <span data-ttu-id="28e09-108">Możesz użyć `-preferreduilang` opcję kompilatora, aby określić język, który chcesz, aby kompilator języka C# do użycia dla komunikatów o błędach i inne dane wyjściowe wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="28e09-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="28e09-109">Jeśli nie zainstalowano pakiet językowy dla języka, ustawień języka systemu operacyjnego jest używana zamiast tego, a nie będzie zgłaszany błąd.</span><span class="sxs-lookup"><span data-stu-id="28e09-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="28e09-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28e09-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e09-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28e09-111">See also</span></span>

- [<span data-ttu-id="28e09-112">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="28e09-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
