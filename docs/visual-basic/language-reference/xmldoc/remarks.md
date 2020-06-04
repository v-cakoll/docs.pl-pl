---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400024"
---
# <a name="remarks-visual-basic"></a>\<remarks> (Visual Basic)
Określa sekcję Uwagi dla elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Opis elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<remarks>` znacznika, aby dodać informacje o typie, uzupełniając informacje określone za pomocą [\<summary>](summary.md) .  
  
 Te informacje są wyświetlane w Przeglądarka obiektów. Aby uzyskać informacje na temat Przeglądarka obiektów, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `<remarks>` znacznika do wyjaśnienia `UpdateRecord` metody.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)
