---
title: -preferreduilang (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 7ebafcf446c9033c93e0c5fa5e11ea2930bd2e1e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602562"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="9662a-102">-preferreduilang (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="9662a-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="9662a-103">Korzystając z `-preferreduilang` opcji kompilatora, można określić język, w którym C# kompilator wyświetla dane wyjściowe, takie jak komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="9662a-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9662a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9662a-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="9662a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9662a-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="9662a-106">[Nazwa języka](/windows/desktop/Intl/language-names) języka do użycia dla danych wyjściowych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9662a-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9662a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9662a-107">Remarks</span></span>  
 <span data-ttu-id="9662a-108">Możesz użyć `-preferreduilang` opcji kompilatora, aby określić język, który ma być używany przez C# kompilator do komunikatów o błędach i innych danych wyjściowych wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9662a-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="9662a-109">Jeśli nie zainstalowano pakietu językowego dla tego języka, zamiast niego zostanie użyte ustawienie język systemu operacyjnego i nie zostanie zgłoszony żaden błąd.</span><span class="sxs-lookup"><span data-stu-id="9662a-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="9662a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9662a-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9662a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9662a-111">See also</span></span>

- [<span data-ttu-id="9662a-112">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="9662a-112">C# Compiler Options</span></span>](./index.md)
