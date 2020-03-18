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
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (Opcje kompilatora C#)
Za pomocą `-preferreduilang` opcji kompilatora, można określić język, w którym kompilator C# wyświetla dane wyjściowe, takie jak komunikaty o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Argumenty  
 `language`  
 [Nazwa języka](/windows/desktop/Intl/language-names) języka, który ma być używany dla danych wyjściowych kompilatora.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą `-preferreduilang` opcji kompilatora można określić język, który ma kompilator C# używać do komunikatów o błędach i innych danych wyjściowych wiersza polecenia. Jeśli pakiet językowy dla języka nie jest zainstalowany, zamiast tego używane jest ustawienie języka systemu operacyjnego i nie jest zgłaszany żaden błąd.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
