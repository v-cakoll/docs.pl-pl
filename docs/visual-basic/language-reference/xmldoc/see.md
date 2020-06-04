---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 380923c2313450afc5745b25eeea6a444705dd3f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411528"
---
# <a name="see-visual-basic"></a>\<see> (Visual Basic)
Określa łącze do innego elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML. `member`musi znajdować się w podwójnym cudzysłowie ("").  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<see>` znacznika, aby określić łącze z tekstu. Użyj, [\<seealso>](seealso.md) Aby wskazać tekst, który może być wyświetlany w sekcji "Zobacz też".  
  
 Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa `<see>` znacznika w `UpdateRecord` sekcji uwagi, aby odwołać się do `DoesRecordExist` metody.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)
