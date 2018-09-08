---
title: '&lt;uprawnienie&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: bcec5d968f5d0c5400c28e772df151b164888a47
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191849"
---
# <a name="ltpermissiongt-visual-basic"></a>&lt;uprawnienie&gt; (Visual Basic)
Określa wymagane uprawnienia dla elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i wykonuje translację `member` nazwę kanoniczną element w danych wyjściowych XML. Ujmij `member` w znaki cudzysłowu ("").  
  
 `description`  
 Opis dostępu do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<permission>` tag do dokumentu jest dostęp do elementu członkowskiego. Użyj <xref:System.Security.PermissionSet> klasy w celu określenia dostępu do elementu członkowskiego.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<permission>` tag do opisywania, które <xref:System.Security.Permissions.FileIOPermission> jest wymagana przez `ReadFile` metody.  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
