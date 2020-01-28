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
ms.openlocfilehash: f3c5997f777c937e9726b271afa0ae6d7a19b37d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744174"
---
# <a name="names-of-assemblies-and-dlls"></a>Nazwy zestawów i bibliotek DLL
Zestaw jest jednostką wdrożenia i tożsamością dla programów kodu zarządzanego. Chociaż zestawy mogą obejmować jeden lub więcej plików, zazwyczaj zestaw mapuje jeden do jednego z biblioteką DLL. W związku z tym, w tej sekcji opisano tylko konwencje nazewnictwa bibliotek DLL, które następnie można mapować na konwencje nazewnictwa zestawów.

 ✔️ Wybierz nazwy bibliotek DLL zestawu, które sugerują duże fragmenty funkcjonalności, takich jak system. Data.

 Nazwy zestawów i bibliotek DLL nie muszą odpowiadać nazwom przestrzeni nazw, ale podczas określania nazw zestawów można przestrzegać nazwy przestrzeni nazw. Dobrą regułą dla kciuka jest nazwa biblioteki DLL na podstawie wspólnego prefiksu przestrzeni nazw zawartych w zestawie. Na przykład zestaw zawierający dwie przestrzenie nazw, `MyCompany.MyTechnology.FirstFeature` i `MyCompany.MyTechnology.SecondFeature`, może być nazywany `MyCompany.MyTechnology.dll`.

 ✔️ ROZWAŻYĆ nazewnictwa bibliotek DLL zgodnie z poniższym wzorcem:

 `<Company>.<Component>.dll`

 gdzie `<Component>` zawiera jedną lub więcej klauzul rozdzielonych kropkami. Na przykład:

 `Litware.Controls.dll`.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
