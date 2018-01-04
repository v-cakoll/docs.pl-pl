---
title: "Równoważność typów i osadzone typy międzyoperacyjne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28203dc428db6a2dd06e9c1e85b64ef80e81ffbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Równoważność typów i osadzone typy międzyoperacyjne
Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], typowe obsługuje środowisko uruchomieniowe języka osadzanie informacji o typie dla typów COM bezpośrednio do zarządzanych zestawów, zwalniając zarządzanych zestawów można uzyskać informacji o typie dla typów COM z zestawy międzyoperacyjne. Ponieważ osadzony typ informacji obejmuje tylko typy i elementy członkowskie, które są rzeczywiście używane przez zestaw zarządzany, dwóch zestawów zarządzanych może być bardzo różne widoki tego samego typu COM. Każdy zestaw zarządzany ma inną <xref:System.Type> obiektu do reprezentowania jego widoku typu COM. Środowisko uruchomieniowe języka wspólnego obsługuje pełnienia roli równoważnika typu między tymi różne widoki dla interfejsów, struktury, wyliczenia i delegaty.  
  
 Pełnienia roli równoważnika typu oznacza, że obiekt COM, który jest przekazywany jeden zestaw zarządzany do innego, mogą być rzutowane na odpowiednie zarządzanego typu w zestawie odbierania.  
  
> [!NOTE]
>  Równoważność typów i osadzone typy międzyoperacyjne we wdrażaniu aplikacji i dodatków, które korzystają ze składników COM, ponieważ nie jest konieczne wdrażanie zestawów międzyoperacyjnych z aplikacjami. Deweloperzy udostępniane składniki COM nadal jest konieczne tworzenie podstawowych zestawów międzyoperacyjnych (PIAs), aby ich składniki do użycia we wcześniejszych wersjach programu .NET Framework.  
  
## <a name="type-equivalence"></a>Pełnienia roli równoważnika typu  
 Równoważność typów COM jest obsługiwana dla interfejsów, struktury, wyliczenia i delegaty. Typy modelu COM kwalifikują się jako równoważne, jeśli spełnione są wszystkie z następujących czynności:  
  
-   Typy są zarówno interfejsów, lub zarówno struktury, lub zarówno wyliczenia lub obu delegatów.  
  
-   Typy mają taką samą tożsamość, zgodnie z opisem w następnej sekcji.  
  
-   Oba typy kwalifikują się do pełnienia roli równoważnika typu, zgodnie z opisem w [oznaczenie typów COM do pełnienia roli równoważnika typu](#type_equiv) sekcji.  
  
### <a name="type-identity"></a>Typ tożsamości  
 Dwa typy są określone na tej samej tożsamości gdy ich zakresów i tożsamości są zgodne, innymi słowy, jeśli mają <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> i atrybutami dwóch zawierają zgodnych <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> i <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> właściwości. Porównanie dla <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> nie uwzględnia wielkości liter.  
  
 Jeśli nie ma typu <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybutu, lub jeśli ma <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybutu, która nie określa zakresu i identyfikator, typ nadal jest uznawana za do pełnienia roli równoważnika w następujący sposób:  
  
-   Dla interfejsów, wartość <xref:System.Runtime.InteropServices.GuidAttribute> jest używany zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> właściwości oraz <xref:System.Type.FullName%2A?displayProperty=nameWithType> (oznacza to, że nazwa typu, łącznie z przestrzenią nazw) jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> właściwości.  
  
-   Struktury, wyliczenia i delegaty <xref:System.Runtime.InteropServices.GuidAttribute> zawierającego zestawu jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> właściwości oraz <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwość jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> właściwości.  
  
<a name="type_equiv"></a>   
### <a name="marking-com-types-for-type-equivalence"></a>Oznaczenie typów COM do pełnienia roli równoważnika typu  
 Można oznaczyć typu jako kwalifikujący się do pełnienia roli równoważnika typu, na dwa sposoby:  
  
-   Zastosuj <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybutu typu.  
  
-   Zmień typ typ importu COM. Interfejs jest typ importu COM, jeśli ma ona <xref:System.Runtime.InteropServices.ComImportAttribute> atrybutu. Interfejs, struktury, wyliczenia lub delegat jest typ importu COM, jeśli występują zestawu, w którym jest zdefiniowany <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Type.IsEquivalentTo%2A>  
 [Używanie typów COM w kodzie zarządzanym](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
