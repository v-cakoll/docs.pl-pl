---
title: Zestawy kolekcjonowane dla dynamicznego generowania typów
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 02c7048e0321282463aa3558287d1d13c5e4f8d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180542"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Zestawy kolekcjonowane dla dynamicznego generowania typów

*Zestawy kolekcjonerskie* to zestawy dynamiczne, które można zwolnić bez zwalniania domeny aplikacji, w której zostały utworzone. Wszystkie zarządzane i niezarządzane pamięci używane przez kolekcjonowane zestawu i typów, które zawiera mogą być odzyskane. Informacje, takie jak nazwa zestawu, są usuwane z tabel wewnętrznych.

Aby włączyć zwalnianie, <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> należy użyć flagi podczas tworzenia zespołu dynamicznego. Zestaw jest przejściowy (to znaczy, że nie można go zapisać) i podlega ograniczeniom opisanym w sekcji [Ograniczenia dotyczące zestawów kolekcjonerskich.](#restrictions-on-collectible-assemblies) Środowisko uruchomieniowe języka wspólnego (CLR) zwalnia kolekcjonowania zestawu automatycznie po zwolnieniu wszystkich obiektów skojarzonych z zestawu. Pod każdym względem zestawy kolekcjonerskie są tworzone i używane w taki sam sposób jak inne zestawy dynamiczne.

## <a name="lifetime-of-collectible-assemblies"></a>Okres istnienia zespołów kolekcjonerskich

Okres istnienia kolekcjonowania zestawu jest kontrolowana przez istnienie odwołań do typów, które zawiera i obiektów, które są tworzone z tych typów. Środowisko uruchomieniowe języka wspólnego nie zwalnia zestawu, o ile`T` istnieje jeden lub więcej z poniższych ( jest dowolnym typem zdefiniowanym w zestawie):

- Wystąpienie elementu `T`.

- Wystąpienie tablicy `T`. .

- Wystąpienie typu ogólnego, `T` który ma jako jeden z jego argumentów typu. Obejmuje to ogólne `T`kolekcje , nawet jeśli ta kolekcja jest pusta.

- Wystąpienie <xref:System.Type> lub <xref:System.Reflection.Emit.TypeBuilder> które `T`reprezentuje .

   > [!IMPORTANT]
   > Należy zwolnić wszystkie obiekty, które reprezentują części złożenia. `T` Definiuje, <xref:System.Reflection.Emit.ModuleBuilder> że zachowuje odwołanie <xref:System.Reflection.Emit.TypeBuilder>do , <xref:System.Reflection.Emit.AssemblyBuilder> i obiekt zachowuje <xref:System.Reflection.Emit.ModuleBuilder>odwołanie do , więc odwołania do tych obiektów musi zostać zwolniony. Nawet istnienie <xref:System.Reflection.Emit.LocalBuilder> lub <xref:System.Reflection.Emit.ILGenerator> wykorzystywane w konstrukcji `T` zapobiega rozładunku.

- Odwołanie statyczne `T` przez inny dynamicznie `T1` zdefiniowany typ, który jest nadal osiągalny przez wykonanie kodu. Na przykład `T1` może pochodzić `T` `T` od lub może być typem `T1`parametru w metodzie .

- A **ByRef** do pola statycznego, `T`które należy do .

- A <xref:System.RuntimeTypeHandle> <xref:System.RuntimeFieldHandle>, <xref:System.RuntimeMethodHandle> lub który `T` odnosi się do `T`lub do składnika .

- Wystąpienie dowolnego obiektu odbicia, który może być używany <xref:System.Type> pośrednio `T`lub bezpośrednio w celu uzyskania dostępu do obiektu, który reprezentuje . Na przykład <xref:System.Type> obiekt `T` dla można uzyskać z typu tablicy, którego typ elementu jest `T`, lub od typu ogólnego, który ma `T` jako argument typu.

- Metoda `M` na stosie wywołań dowolnego `M` wątku, `T` gdzie jest metodą lub metodą na poziomie modułu, która jest zdefiniowana w zestawie.

- Delegat do metody statycznej, która jest zdefiniowana w module zestawu.

Jeśli istnieje tylko jeden element z tej listy tylko dla jednego typu lub jednej metody w zestawie, środowisko wykonawcze nie może zwolnić zestawu.

> [!NOTE]
> Środowisko wykonawcze faktycznie nie zwalnia zestawu, dopóki finalizatory nie uruchomią dla wszystkich elementów na liście.

Na potrzeby śledzenia okresu istnienia, skonstruowany `List<int>` typ ogólny, takich `List(Of Integer)` jak (w języku C#) lub (w języku Visual Basic), który jest tworzony i używany w generowaniu zestawu kolekcjonowania jest uważany za zdefiniowany w zestawie, który zawiera definicję typu ogólnego lub w zestawie, który zawiera definicję jednego z jego argumentów typu. Dokładny zestaw, który jest używany jest szczegół implementacji i może ulec zmianie.

## <a name="restrictions-on-collectible-assemblies"></a>Ograniczenia dotyczące zespołów kolekcjonerskich

Do zestawów kolekcjonerskich obowiązują następujące ograniczenia:

- **Odniesienia statyczne** Typy w zwykłym złożeniu dynamicznym nie mogą mieć statycznych odwołań do typów, które są zdefiniowane w kolekcjonuje. Na przykład jeśli zdefiniujesz zwykły typ, który dziedziczy z <xref:System.NotSupportedException> typu w kolekcjonowania zestawu, wyjątek. Typ w kolekcjonowania zestawu może mieć statyczne odwołania do typu w innym zestawie kolekcjonerskich, ale to wydłuża okres istnienia zestawu, do którego istnieje odwołanie do okresu istnienia zestawu odwołującego się.

- **Współdziałacze COM** Żadne interfejsy COM nie mogą być zdefiniowane w kolekcjonowania zestawu i żadnych wystąpień typów w kolekcjonowania zestawu mogą być konwertowane na obiekty COM. Typ w kolekcjonowania zestawu nie może służyć jako com wywoływane otoki (CCW) lub wywoływane otoki (RCW). Jednak typy w zestawach kolekcjonerskich można używać obiektów, które implementują interfejsy COM.

- **Wywołanie platformy** Metody, które <xref:System.Runtime.InteropServices.DllImportAttribute> mają atrybut nie będzie kompilować, gdy są one zadeklarowane w kolekcjonowania zestawu. Instrukcja <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> nie może służyć do implementacji typu w kolekcjonerów zestawu i takich typów nie można zorganizować do kodu niezarządzanego. Jednak można wywołać do kodu macierzystego przy użyciu punktu wejścia, który jest zadeklarowany w zestawie niezbieralne.

- **Kierowanie** Nie można marshal obiektami (w szczególności delegatów), które są zdefiniowane w zestawach kolekcjonerskich. Jest to ograniczenie dla wszystkich typów emitowanych przejściowych.

- **Obciążenie zespołu** Odbicie emitować jest jedynym mechanizmem, który jest obsługiwany do ładowania zestawów kolekcjonerskich. Nie można zwolnić zestawów, które są ładowane przy użyciu innych form załadunku złożenia.

- **Obiekty powiązane kontekstem** Zmienne statyczne kontekstu nie są obsługiwane. Typy w kolekcjonuje <xref:System.ContextBoundObject>zestaw nie można rozszerzyć . Jednak kod w zestawach kolekcjonerskich można użyć obiektów związanych z kontekstem, które są zdefiniowane w innym miejscu.

- **Dane statyczne wątku** Zmienne statyczne wątku nie są obsługiwane.

## <a name="see-also"></a>Zobacz też

- [Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)
