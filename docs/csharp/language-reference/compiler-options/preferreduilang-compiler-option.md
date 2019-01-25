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
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
