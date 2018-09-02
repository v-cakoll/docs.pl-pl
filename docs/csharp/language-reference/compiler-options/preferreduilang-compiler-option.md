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
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (opcje kompilatora C#)
Za pomocą `-preferreduilang` — opcja kompilatora, można określić język, w którym kompilator języka C#, wyświetla dane wyjściowe, takie jak komunikaty o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Argumenty  
 `language`  
 [Nazwa języka](/windows/desktop/Intl/language-names) języka do użycia dla danych wyjściowych kompilatora.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `-preferreduilang` opcję kompilatora, aby określić język, który chcesz, aby kompilator języka C# do użycia dla komunikatów o błędach i inne dane wyjściowe wiersza polecenia. Jeśli nie zainstalowano pakiet językowy dla języka, ustawień języka systemu operacyjnego jest używana zamiast tego, a nie będzie zgłaszany błąd.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
