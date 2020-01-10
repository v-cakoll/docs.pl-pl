---
title: Nazwy zestawów i bibliotek DLL
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: eebccba0b923b04333f289a85330d190c31013ab
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709260"
---
# <a name="names-of-assemblies-and-dlls"></a>Nazwy zestawów i bibliotek DLL
Zestaw jest jednostką wdrożenia i tożsamością dla programów kodu zarządzanego. Chociaż zestawy mogą obejmować jeden lub więcej plików, zazwyczaj zestaw mapuje jeden do jednego z biblioteką DLL. W związku z tym, w tej sekcji opisano tylko konwencje nazewnictwa bibliotek DLL, które następnie można mapować na konwencje nazewnictwa zestawów.  
  
 **✓ DO** wybierz nazw dla Twojego zestawu bibliotek DLL, które sugeruje duże zestawy funkcji, takich jak dane systemowe.  
  
 Nazwy zestawów i bibliotek DLL nie muszą odpowiadać nazwom przestrzeni nazw, ale podczas określania nazw zestawów można przestrzegać nazwy przestrzeni nazw. Dobrą regułą dla kciuka jest nazwa biblioteki DLL na podstawie wspólnego prefiksu przestrzeni nazw zawartych w zestawie. Na przykład zestaw zawierający dwie przestrzenie nazw, `MyCompany.MyTechnology.FirstFeature` i `MyCompany.MyTechnology.SecondFeature`, może być nazywany `MyCompany.MyTechnology.dll`.  
  
 **✓ CONSIDER** nazewnictwa bibliotek DLL według następującego wzorca:  
  
 `<Company>.<Component>.dll`  
  
 gdzie `<Component>` zawiera jedną lub więcej klauzul rozdzielonych kropkami. Na przykład:  
  
 `Litware.Controls.dll`.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
