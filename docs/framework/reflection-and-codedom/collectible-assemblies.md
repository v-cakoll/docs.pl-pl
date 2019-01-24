---
title: Zestawy kolekcjonowane dla dynamicznego generowania typów
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b26da264b2da40e19db4bc5e3b3575505f5c979c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637745"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Zestawy kolekcjonowane dla dynamicznego generowania typów

*Zestawy kolekcjonowane* dynamicznych zestawów, które może być rozładowany bez rozładowywania domeny aplikacji, w którym zostały utworzone. Można odzyskać całej pamięci zarządzane i niezarządzane używane przez zestaw kolekcjonowany i typy, które zawiera. Informacje, takie jak nazwa zestawu jest usuwany z tabel wewnętrznych.

Do włączenia zwalniania, użyj <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> Flaga podczas tworzenia zestawu dynamicznego. Zestaw jest przejściowy (oznacza to, że nie można zapisać go) i może ulec ograniczenia opisane w [ograniczenia dotyczące zestawy Kolekcjonowane](#restrictions-on-collectible-assemblies) sekcji. Środowisko uruchomieniowe języka wspólnego (CLR) zwalnia zestaw kolekcjonowany automatycznie po zwolnieniu wszystkie obiekty skojarzone z zestawem. Pod innymi względami zestawy kolekcjonowane są tworzone i używane w taki sam sposób jak inne zestawów dynamicznych.

## <a name="lifetime-of-collectible-assemblies"></a>Okres istnienia zestawy kolekcjonowane

Okres istnienia zestaw kolekcjonowany jest kontrolowana przez istnienie odwołania do typów, które zawiera i obiekty, które są tworzone na podstawie tych typów. Środowisko uruchomieniowe języka wspólnego nie spowoduje usunięcia zestawu, tak długo, jak istnieje co najmniej jeden z następujących czynności (`T` jest dowolny typ, który jest zdefiniowany w zestawie): 

- Wystąpienie `T`.

- Wystąpienie tablicy `T`.
 
- Wystąpienia typu ogólnego, który ma `T` jako jeden z argumentów typu. W tym ogólnych kolekcji `T`nawet wtedy, gdy tej kolekcji jest pusta.

- Wystąpienie <xref:System.Type> lub <xref:System.Reflection.Emit.TypeBuilder> reprezentujący `T`. 

   > [!IMPORTANT]
   > Konieczne jest zwolnienie wszystkich obiektów, które reprezentuje części zestawu. <xref:System.Reflection.Emit.ModuleBuilder> Definiujący `T` przechowuje odwołania do <xref:System.Reflection.Emit.TypeBuilder>i <xref:System.Reflection.Emit.AssemblyBuilder> obiekt przechowuje odwołania do <xref:System.Reflection.Emit.ModuleBuilder>, więc odwołania do tych obiektów, które muszą zostać zwolnione. Nawet istnienie <xref:System.Reflection.Emit.LocalBuilder> lub <xref:System.Reflection.Emit.ILGenerator> używany do budowy `T` zapobiega zwolnienie.

- Statyczne odwołanie do `T` przez inny typ dynamicznie definiowane `T1` , jest nadal dostępny przy wykonywaniu kodu. Na przykład `T1` może pochodzić od `T`, lub `T` może być typem parametru w metodzie o `T1`.
 
- A **ByRef** w polu statycznym, który należy do `T`.

- A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, lub <xref:System.RuntimeMethodHandle> odwołujący się do `T` lub składnik `T`.

- Wystąpienia dowolnego obiektu odbicia, która mogłaby być używana pośrednio lub bezpośrednio do dostępu <xref:System.Type> obiekt, który reprezentuje `T`. Na przykład <xref:System.Type> dla obiektu `T` można uzyskać z typem tablicy, którego typ elementu jest `T`, lub z typu ogólnego, który ma `T` jako argument typu. 

- Metody `M` w stosie wywołań z żadnym z wątków, gdzie `M` to metoda `T` lub metoda poziom modułu, która jest zdefiniowana w zestawie.

- Delegat na metodę statyczną, która jest zdefiniowana w module tego zestawu.

Jeśli tylko jeden element z tej listy istnieje tylko jeden typ lub jednej metody w zestawie, środowisko uruchomieniowe nie może zwolnić zestaw.

> [!NOTE]
> Środowisko uruchomieniowe nie faktycznie zwolnić zestaw, do momentu finalizatory zostały uruchomione dla wszystkich elementów na liście.

W celu śledzenia okresu istnienia, zbudowany typ ogólny takich jak `List<int>` (w C#) lub `List(Of Integer)` (w języku Visual Basic), są tworzone i używane w generacji zestaw kolekcjonowany uznaje się za zdefiniowana w zestawie zawiera definicji typu ogólnego lub w zestawie, który zawiera definicję jednego z argumentów typu. Dokładny zestaw, który jest używany jest szczegółowo opisuje implementacja i ulegną zmianie.
 
## <a name="restrictions-on-collectible-assemblies"></a>Ograniczenia dotyczące zestawy kolekcjonowane

Aby zestawy kolekcjonowane są stosowane następujące ograniczenia: 

- **Odwołań statycznych**   
  Typy w zwykłych zestawu dynamicznego nie może mieć statyczne odwołania do typów, które są zdefiniowane w zestawie. Na przykład, jeśli zdefiniujesz zwykły typ, który dziedziczy z typu w zestawie kolekcjonowane <xref:System.NotSupportedException> wyjątku. Typ w zestawie mogą mieć statyczne odwołania do typu w innym zestawie, ale spowoduje to rozszerzenie okres istnienia przywoływanego zestawu z okresem istnienia zestaw odwołujący się.

- **Usługa międzyoperacyjna modelu COM**   
   Interfejsy modelu COM nie mogą być definiowane w zestawie, a nie wystąpień typów w zestawie mogą być konwertowane na obiekty COM. Typ w zestawie nie może służyć jako wywoływana otoka COM (CCW) lub wywoływana otoka środowiska uruchomieniowego (RCW). Jednak typów w zestawach kolekcjonowane można użyć obiektów, które implementują interfejsy COM.

- **Wywołanie platformy**   
   Metody, które mają <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut nie zostanie skompilowany, gdy są deklarowane w zestawie. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> Nie może być używana w celu wykonania danego typu w zestawie i takich typów nie mogą być przekazywane do kodu niezarządzanego. Można jednak wywoływać kodu natywnego za pomocą punktu wejścia, który jest zadeklarowany w zestawie kolekcjonowane.
 
- **marshaling**   
   Obiekty (w szczególności delegatów), które są zdefiniowane w zestawy kolekcjonowane nie mogą być przekazywane. Jest to ograniczenie dla wszystkich typów emitowany przejściowy.

- **Ładowanie zestawu**   
   Emisji odbicia jest tylko mechanizm, który jest obsługiwany w przypadku ładowania zestawy kolekcjonowane. Zestawy, które są ładowane przy użyciu innej formy z ładowaniem zestawu, nie można zwolnić.
 
- **Obiekty powiązane ze kontekstu**    
   Zmienne statyczne kontekstu nie są obsługiwane. Typy w zestawie nie można rozszerzyć <xref:System.ContextBoundObject>. Jednak kod w zestawy kolekcjonowane wykorzystać obiekty powiązane z kontekstu, które są zdefiniowane gdzie indziej.

- **Dane statyczne wątku**       
   Zmienne statyczne wątku nie są obsługiwane.

## <a name="see-also"></a>Zobacz także

- [Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)
