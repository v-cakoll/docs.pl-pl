---
title: "Zestawów kolekcjonowanych generacji typu dynamicznego"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c9a613f4cc13c3e4189a59ace2e05d01d1bcb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Zestawów kolekcjonowanych generacji typu dynamicznego

*Zestawów kolekcjonowanych* są dynamiczne zestawy, które może być zwolniony bez zwalniania domeny aplikacji, w którym zostały utworzone. Można odzyskać wszystkie zarządzane i niezarządzane pamięci używanej przez zestawu kolekcjonowanego i typy, które zawiera. Informacje takie jak nazwa zestawu jest usuwany z wewnętrznego tabel.

Aby włączyć zwalnianie, należy użyć <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> Flaga podczas tworzenia zestawu dynamicznego. Zestaw jest przejściowy (to znaczy, że nie można jej zapisać) i ograniczenia opisane w tym podlega [ograniczenia dotyczące zestawów kolekcjonowanych](#restrictions-on-collectible-assemblies) sekcji. Środowisko uruchomieniowe języka wspólnego (CLR) zwalnia zestawu kolekcjonowanego automatycznie po zwolnieniu wszystkie obiekty skojarzone z zestawu. We wszystkich innych aspektach zestawów kolekcjonowanych są tworzone i używane w taki sam sposób jak inne zestawów dynamicznych.

## <a name="lifetime-of-collectible-assemblies"></a>Okres istnienia zestawów kolekcjonowanych

Okres istnienia zestawu kolekcjonowanego jest kontrolowana przez istnienie odwołania do typów, które zawiera i obiekty, które są tworzone na podstawie tych typów. Środowisko uruchomieniowe języka wspólnego nie spowoduje usunięcia zestawu tak długo, jak istnieje co najmniej jeden z następujących (`T` jest dowolnego typu, który jest zdefiniowany w zestawie): 

- Wystąpienie `T`.

- Wystąpienia tablicy `T`.
 
- Wystąpienie typu ogólnego, który ma `T` jako jeden z jego argumentów typu. Dotyczy to również ogólne kolekcje `T`nawet w przypadku tej kolekcji jest pusty.

- Wystąpienie <xref:System.Type> lub <xref:System.Reflection.Emit.TypeBuilder> reprezentujący `T`. 

   > [!IMPORTANT]
   > Konieczne jest zwolnienie wszystkich obiektów, które reprezentują części zestawu. <xref:System.Reflection.Emit.ModuleBuilder> Definiuje `T` przechowuje odwołanie do <xref:System.Reflection.Emit.TypeBuilder>i <xref:System.Reflection.Emit.AssemblyBuilder> obiekt przechowuje odwołanie do <xref:System.Reflection.Emit.ModuleBuilder>, więc musi zostać zwolniona odwołania do tych obiektów. Nawet istnienie <xref:System.Reflection.Emit.LocalBuilder> lub <xref:System.Reflection.Emit.ILGenerator> używany do budowy `T` uniemożliwia zwalnianie.

- Statyczne odwołanie do `T` za pomocą innego typu dynamicznie zdefiniowanych `T1` jest nadal dostępny przez wykonywanie kodu. Na przykład `T1` może pochodzić od `T`, lub `T` może być typem parametru w metodzie `T1`.
 
- A **ByRef** w polu statycznym, który należy do `T`.

- A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, lub <xref:System.RuntimeMethodHandle> odwołujący się do `T` lub składnik `T`.

- Wystąpienia dowolnego obiektu odbicia, które mogą zostać użyte pośrednio lub bezpośrednio do dostępu <xref:System.Type> obiekt, który reprezentuje `T`. Na przykład <xref:System.Type> obiekt do `T` można uzyskać z typem tablicy o typie elementu `T`, lub z typu ogólnego, który ma `T` jako argument typu. 

- Metody `M` w stosie wywołań z dowolnego wątku, gdzie `M` jest metodą `T` lub metody poziom modułu, który jest zdefiniowany w zestawie.

- Delegat metody statycznej, który jest zdefiniowany w module tego zestawu.

Jeśli tylko jeden element z tej listy istnieje tylko jeden typ lub jednej metody w zestawie, środowisko uruchomieniowe nie może zwolnić zestawu.

> [!NOTE]
> Środowisko uruchomieniowe nie powoduje faktycznie zwolnienia zestawu, do momentu finalizatory zostały przeprowadzone dla wszystkich elementów na liście.

W celu śledzenia okres istnienia, skonstruowane ogólny wpisz na przykład `List<int>` (w języku C#) lub `List(Of Integer)` (w języku Visual Basic) który są tworzone i używane w Generowanie zestawu kolekcjonowanego jest uznawany za zostały zdefiniowane w zestawie który zawiera ogólnych definicji typu lub w zestawie, który zawiera definicję jednego z jego argumentów typu. Dokładne zestawu, który jest używany jest szczegóły implementacji i ulegną zmianie.
 
## <a name="restrictions-on-collectible-assemblies"></a>Ograniczenia dotyczące zestawów kolekcjonowanych

Do zestawów kolekcjonowanych, obowiązują następujące ograniczenia: 

- **Statyczne odwołań**   
  Typy w zestawie dynamicznym zwykłej nie mogą mieć statycznych odwołania do typów, które są zdefiniowane w zestawu kolekcjonowanego. Na przykład w przypadku definiowania zwykłej typu, który dziedziczy z typu w zestawie kolekcjonowanych <xref:System.NotSupportedException> wyjątku. Typ w zestawu kolekcjonowanego może mieć statyczne odwołania do typu w innym zestawie kolekcjonowanych, ale powoduje rozszerzenie okres istnienia przywoływanego zestawu do istnienia odwołaniem do zestawu.

- **Współdziałanie z COM**   
   Interfejsy modelu COM, nie może zostać zdefiniowany w ramach zestawu kolekcjonowanego, a nie wystąpień typów wewnątrz zestawów kolekcjonowanych można przekonwertować na obiekty COM. Typ w zestawu kolekcjonowanego nie może służyć jako wywoływana otoka COM (CCW) lub wywoływana otoka środowiska uruchomieniowego (otoki RCW). Jednak typów w zestawach kolekcjonowanych można użyć obiektów implementujących interfejsy modelu COM.

- **Wywołanie platformy**   
   Metody, które mają <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut nie zostanie skompilowany, gdy są one zgłoszone w zestawu kolekcjonowanego. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> Nie może być używana w implementacji typu w zestawu kolekcjonowanego i takich typów nie mogą być przekazywane do kodu niezarządzanego. Można jednak wywoływać kodu natywnego, przy użyciu punktu wejścia, które są zadeklarowane w zestaw niekolekcjonowany.
 
- **Organizowanie**   
   Obiekty (w szczególności, delegatów), które są zdefiniowane w zestawów kolekcjonowanych nie mogą być przekazywane. To ograniczenie na wszystkich typach emitowany przejściowej.

- **Podczas ładowania zestawu**   
   Emisja odbicia jest tylko mechanizm, który jest obsługiwany w przypadku ładowania zestawów kolekcjonowanych. Zestawy, które są ładowane przy użyciu jakąkolwiek inną formę ładowania zestawu nie może być usunięty z pamięci.
 
- **Obiekty związane z kontekstem**    
   Zmienne statyczne kontekstu nie są obsługiwane. Typy w zestawu kolekcjonowanego nie może rozszerzać <xref:System.ContextBoundObject>. Jednak kod w zestawów kolekcjonowanych użyć obiekty związane z kontekstem, które są zdefiniowane w innym miejscu.

- **Dane statyczne dla wątku**       
   Zmienne statyczne dla wątku nie są obsługiwane.

## <a name="see-also"></a>Zobacz także

[Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)
