---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 7333d4a4d051c157f6732224da0fffe4d7cd35ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827669"
---
# <a name="permission-visual-basic"></a>\<uprawnienie > (Visual Basic)
Określa wymagane uprawnienia dla elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i wykonuje translację `member` nazwę kanoniczną element w danych wyjściowych XML. Ujmij `member` w znaki cudzysłowu ("").  
  
 `description`  
 Opis dostępu do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<permission>` tag do dokumentu jest dostęp do elementu członkowskiego. Użyj <xref:System.Security.PermissionSet> klasy w celu określenia dostępu do elementu członkowskiego.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<permission>` tag do opisywania, które <xref:System.Security.Permissions.FileIOPermission> jest wymagana przez `ReadFile` metody.  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
