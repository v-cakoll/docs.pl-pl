---
title: Chronione składowe
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 14ef02a760c9d4b77fe058334baffd63fcf29cfd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709104"
---
# <a name="protected-members"></a>Chronione składowe
Chronione elementy członkowskie nie zapewniają żadnych rozszerzalności, ale mogą zwiększyć możliwości rozszerzania za pomocą podklas. Mogą one służyć do udostępnienia zaawansowanych opcji dostosowania bez niepotrzebnego skomplikowania głównego interfejsu publicznego.  
  
 Projektantom struktury należy zachować ostrożność z chronionymi elementami członkowskimi, ponieważ nazwa "Protected" może mieć fałszywe znaczenie dla zabezpieczeń. Każda osoba może poddawać podklasie niezapieczętowanej klasie i uzyskać dostęp do chronionych elementów członkowskich, dzięki czemu wszystkie takie same praktyki dotyczące kodowania, które są używane dla publicznych członków, mają zastosowanie do chronionych elementów członkowskich.  
  
 **✓ CONSIDER** przy użyciu chronione elementy członkowskie dostosowania zaawansowanego.  
  
 **✓ DO** Traktuj chronionych elementów członkowskich w klasach otwarty jako public na potrzeby analizy zabezpieczeń, dokumentacji i zgodności.  
  
 Każdy może dziedziczyć z klasy i uzyskiwać dostęp do chronionych elementów członkowskich.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
