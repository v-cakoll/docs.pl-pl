---
title: Równoważność typów i osadzone typy międzyoperacyjne
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3eeba609349bb9d5b7c68e15e0e0e6ff3f1b7ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390936"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Równoważność typów i osadzone typy międzyoperacyjne

Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], typowe obsługuje środowisko uruchomieniowe języka osadzanie informacji o typie dla typów COM bezpośrednio do zarządzanych zestawów, zwalniając zarządzanych zestawów można uzyskać informacji o typie dla typów COM z zestawy międzyoperacyjne. Ponieważ osadzony typ informacji obejmuje tylko typy i elementy członkowskie, które są rzeczywiście używane przez zestaw zarządzany, dwóch zestawów zarządzanych może być bardzo różne widoki tego samego typu COM. Każdy zestaw zarządzany ma inną <xref:System.Type> obiektu do reprezentowania jego widoku typu COM. Środowisko uruchomieniowe języka wspólnego obsługuje pełnienia roli równoważnika typu między tymi różne widoki dla interfejsów, struktury, wyliczenia i delegaty.

Pełnienia roli równoważnika typu oznacza, że obiekt COM, który jest przekazywany jeden zestaw zarządzany do innego, mogą być rzutowane na odpowiednie zarządzanego typu w zestawie odbierania.

> [!NOTE]
> Równoważność typów i osadzone typy międzyoperacyjne we wdrażaniu aplikacji i dodatków, które korzystają ze składników COM, ponieważ nie jest konieczne wdrażanie zestawów międzyoperacyjnych z aplikacjami. Deweloperzy udostępniane składniki COM nadal jest konieczne tworzenie podstawowych zestawów międzyoperacyjnych (PIAs), aby ich składniki do użycia we wcześniejszych wersjach programu .NET Framework.

## <a name="type-equivalence"></a>Pełnienia roli równoważnika typu

 Równoważność typów COM jest obsługiwana dla interfejsów, struktury, wyliczenia i delegaty. Typy modelu COM kwalifikują się jako równoważne, jeśli spełnione są wszystkie z następujących czynności:

- Typy są zarówno interfejsów, lub zarówno struktury, lub zarówno wyliczenia lub obu delegatów.

- Typy mają taką samą tożsamość, zgodnie z opisem w następnej sekcji.

- Oba typy kwalifikują się do pełnienia roli równoważnika typu, zgodnie z opisem w [typów COM oznaczenie do pełnienia roli równoważnika typu](#marking-com-types-for-type-equivalence) sekcji.

### <a name="type-identity"></a>Typ tożsamości

Dwa typy są określone na tej samej tożsamości gdy ich zakresów i tożsamości są zgodne, innymi słowy, jeśli mają <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> i atrybutami dwóch zawierają zgodnych <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> i <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> właściwości. Porównanie dla <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> nie uwzględnia wielkości liter.

Jeśli nie ma typu <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybutu, lub jeśli ma <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybutu, która nie określa zakresu i identyfikator, typ nadal jest uznawana za do pełnienia roli równoważnika w następujący sposób:

- Dla interfejsów, wartość <xref:System.Runtime.InteropServices.GuidAttribute> jest używany zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> właściwości oraz <xref:System.Type.FullName%2A?displayProperty=nameWithType> (oznacza to, że nazwa typu, łącznie z przestrzenią nazw) jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> właściwości.

- Struktury, wyliczenia i delegaty <xref:System.Runtime.InteropServices.GuidAttribute> zawierającego zestawu jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> właściwości oraz <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwość jest używana zamiast <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> właściwości.

### <a name="marking-com-types-for-type-equivalence"></a>Oznaczenie typów COM do pełnienia roli równoważnika typu

 Można oznaczyć typu jako kwalifikujący się do pełnienia roli równoważnika typu, na dwa sposoby:

- Zastosuj <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> atrybutu typu.

- Zmień typ typ importu COM. Interfejs jest typ importu COM, jeśli ma ona <xref:System.Runtime.InteropServices.ComImportAttribute> atrybutu. Interfejs, struktury, wyliczenia lub delegat jest typ importu COM, jeśli występują zestawu, w którym jest zdefiniowany <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> atrybutu.

## <a name="see-also"></a>Zobacz także

<xref:System.Type.IsEquivalentTo%2A>  
[Używanie typów COM w kodzie zarządzanym](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
[Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)  
