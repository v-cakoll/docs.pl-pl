---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: b3acec04060367a0b9e54b19c0106644d028357b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400037"
---
# <a name="permission-visual-basic"></a>\<permission> (Visual Basic)
Określa wymagane uprawnienie dla elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML. Należy ująć `member` w cudzysłów ("").  
  
 `description`  
 Opis dostępu do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<permission>` znacznika, aby udokumentować dostęp do elementu członkowskiego. Użyj <xref:System.Security.PermissionSet> klasy, aby określić dostęp do elementu członkowskiego.  
  
 Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `<permission>` znacznika do opisania, że <xref:System.Security.Permissions.FileIOPermission> jest wymagane przez `ReadFile` metodę.  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)
