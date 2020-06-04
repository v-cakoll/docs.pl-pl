---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 893ed299b46bd6255ca0e87d008ac53265698614
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411502"
---
# <a name="summary-visual-basic"></a>\<summary> (Visual Basic)
Określa podsumowanie elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Podsumowanie obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<summary>` znacznika, aby opisać typ lub element członkowski typu. Służy [\<remarks>](remarks.md) do dodawania dodatkowych informacji do opisu typu.  
  
 Tekst `<summary>` znacznika jest jedynym źródłem informacji o typie w technologii IntelliSense i jest również wyświetlany w Przeglądarka obiektów. Aby uzyskać informacje na temat Przeglądarka obiektów, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `<summary>` znacznika do opisania `ResetCounter` metody i `Counter` właściwości.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)
