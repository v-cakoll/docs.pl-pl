---
title: <value> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 1a1a4beb4a3412fe7739a69ecd0fed650b332fb2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263946"
---
# <a name="value-c-programming-guide"></a>\<wartość > (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametry  
 `property-description`  
 Opis właściwości.  
  
## <a name="remarks"></a>Uwagi  
 \<Wartość > znacznik umożliwia opisują wartość, która reprezentuje właściwość. Należy pamiętać, że po dodaniu właściwości za pomocą Kreatora kodów w środowisku programowania Visual Studio .NET, spowoduje to dodanie [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) tag w przypadku nowej właściwości. Następnie należy ręcznie dodać \<wartość > tag do opisania wartość, która reprezentuje właściwość.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
