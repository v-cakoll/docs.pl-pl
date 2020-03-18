---
title: -preferreduilang (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 7ebafcf446c9033c93e0c5fa5e11ea2930bd2e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602562"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="bca1a-102">-preferreduilang (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="bca1a-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="bca1a-103">Za pomocą `-preferreduilang` opcji kompilatora, można określić język, w którym kompilator C# wyświetla dane wyjściowe, takie jak komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="bca1a-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bca1a-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="bca1a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bca1a-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="bca1a-106">[Nazwa języka](/windows/desktop/Intl/language-names) języka, który ma być używany dla danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="bca1a-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca1a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bca1a-107">Remarks</span></span>  
 <span data-ttu-id="bca1a-108">Za pomocą `-preferreduilang` opcji kompilatora można określić język, który ma kompilator C# używać do komunikatów o błędach i innych danych wyjściowych wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bca1a-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="bca1a-109">Jeśli pakiet językowy dla języka nie jest zainstalowany, zamiast tego używane jest ustawienie języka systemu operacyjnego i nie jest zgłaszany żaden błąd.</span><span class="sxs-lookup"><span data-stu-id="bca1a-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="bca1a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bca1a-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca1a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bca1a-111">See also</span></span>

- [<span data-ttu-id="bca1a-112">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="bca1a-112">C# Compiler Options</span></span>](./index.md)
