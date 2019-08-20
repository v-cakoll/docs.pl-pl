---
title: <seealso> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: 3ddaa7efec2b4bf5ffa53971aa6f380a1be9bad8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587656"
---
# <a name="seealso-c-programming-guide"></a>\<seealso — > (C# Przewodnik programowania)
## <a name="syntax"></a>Składnia  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.`member` musi znajdować się w podwójnym cudzysłowie ("").  
  
 Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [ \<temat >](./see.md).  
  
## <a name="remarks"></a>Uwagi  
 Tag \<> seealso — umożliwia określenie tekstu, który może być wyświetlany w sekcji Zobacz też. Użyj >, aby określić łącze z tekstu. [ \<](./see.md)  
  
 Kompiluj z [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 \< [ Zobacz\<> podsumowujące](./summary.md) , aby zapoznać się z przykładem użycia usługi seealso — >.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
