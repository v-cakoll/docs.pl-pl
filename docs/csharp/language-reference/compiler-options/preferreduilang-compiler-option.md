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
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (C# opcje kompilatora)
Korzystając z `-preferreduilang` opcji kompilatora, można określić język, w którym C# kompilator wyświetla dane wyjściowe, takie jak komunikaty o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Argumenty  
 `language`  
 [Nazwa języka](/windows/desktop/Intl/language-names) języka do użycia dla danych wyjściowych kompilatora.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `-preferreduilang` opcji kompilatora, aby określić język, który ma być używany przez C# kompilator do komunikatów o błędach i innych danych wyjściowych wiersza polecenia. Jeśli nie zainstalowano pakietu językowego dla tego języka, zamiast niego zostanie użyte ustawienie język systemu operacyjnego i nie zostanie zgłoszony żaden błąd.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
