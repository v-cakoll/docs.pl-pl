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
ms.openlocfilehash: ccf25e9a5d5d025f9024519b41c4afa17a5081f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="preferreduilang-c-compiler-options"></a>/preferreduilang (opcje kompilatora C#)
Za pomocą `/preferreduilang` — opcja kompilatora, można określić język, w którym kompilator języka C# Wyświetla dane wyjściowe, takie jak komunikaty o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a>Argumenty  
 `language`  
 [Nazwy języka](http://go.microsoft.com/fwlink/p/?LinkId=236992) język do użycia dla danych wyjściowych kompilatora.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `/preferreduilang` opcję kompilatora, aby określić język, który ma komunikaty o błędach i innych wiersza polecenia dane wyjściowe kompilatora C#. Jeśli nie zainstalowano pakiet językowy dla języka, zamiast niego jest używana z ustawieniem języka systemu operacyjnego i nie będzie zgłaszany błąd.  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
