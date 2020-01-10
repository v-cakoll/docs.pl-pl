---
title: <permission> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 67e9d398d1bb43d480f8ca56733106e0f0a22731
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696574"
---
# <a name="permission-c-programming-guide"></a>> uprawnień \<(C# Przewodnik programowania)
## <a name="syntax"></a>Składnia  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>Parametry  
 cref = "`member`"  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML. *składowa* musi znajdować się w podwójnym cudzysłowie ("").  
  
 Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [\<see >](./see.md).  
  
 `description`  
 Opis dostępu do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Tag > uprawnień \<umożliwia dokumentowanie dostępu do elementu członkowskiego. Klasa <xref:System.Security.PermissionSet> pozwala określić dostęp do elementu członkowskiego.  
  
 Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
