---
title: Zestawy kolekcjonowane dla dynamicznego generowania typów
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 85eacff22cf2e1c0b8c3d74a4971de035dfafbe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130290"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Zestawy kolekcjonowane dla dynamicznego generowania typów

*Zestawy kolekcjonowane* to zestawy dynamiczne, które można zwolnić bez zwalniania domeny aplikacji, w której zostały utworzone. Cała zarządzana i niezarządzana pamięć używana przez zestaw kolekcjonowany i typy, które zawiera, można odzyskiwać. Informacje, takie jak nazwa zestawu, są usuwane z tabel wewnętrznych.

Aby włączyć zwalnianie, Użyj flagi <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> podczas tworzenia zestawu dynamicznego. Zestaw jest przejściowy (oznacza to, że nie można go zapisać) i podlega ograniczeniom opisanym w sekcji [ograniczenia dotyczące zestawów kolekcjonowanych](#restrictions-on-collectible-assemblies) . Środowisko uruchomieniowe języka wspólnego (CLR) zwalnia zestaw kolekcjonowany automatycznie po zwolnieniu wszystkich obiektów skojarzonych z zestawem. We wszystkich innych aspektach zestawy kolekcjonowane są tworzone i używane w taki sam sposób jak inne zestawy dynamiczne.

## <a name="lifetime-of-collectible-assemblies"></a>Okres istnienia zestawów kolekcjonowanych

Okres istnienia zestawu kolekcjonowanego jest kontrolowany przez istnienie odwołań do typów, które zawiera, oraz obiektów, które są tworzone na podstawie tych typów. Środowisko uruchomieniowe języka wspólnego nie zwalnia zestawu, tak długo, jak istnieje co najmniej jeden z następujących elementów (`T` jest dowolnym typem zdefiniowanym w zestawie): 

- Wystąpienie `T`.

- Wystąpienie tablicy `T`.
 
- Wystąpienie typu ogólnego, który ma `T` jako jeden z argumentów typu. Obejmuje to ogólne kolekcje `T`, nawet jeśli ta kolekcja jest pusta.

- Wystąpienie <xref:System.Type> lub <xref:System.Reflection.Emit.TypeBuilder>, które reprezentuje `T`. 

   > [!IMPORTANT]
   > Należy zwolnić wszystkie obiekty, które reprezentują części zestawu. <xref:System.Reflection.Emit.ModuleBuilder> definiujący `T` zachowuje odwołanie do <xref:System.Reflection.Emit.TypeBuilder>, a obiekt <xref:System.Reflection.Emit.AssemblyBuilder> przechowuje odwołanie do <xref:System.Reflection.Emit.ModuleBuilder>, więc odwołania do tych obiektów muszą zostać wydane. Nawet istnienie <xref:System.Reflection.Emit.LocalBuilder> lub <xref:System.Reflection.Emit.ILGenerator> używane w konstrukcji `T` zapobiega wyładowaniu.

- Statyczne odwołanie do `T` przez inny typ dynamicznie zdefiniowany `T1`, który jest nadal dostępny przez wykonywanie kodu. Na przykład `T1` mogą pochodzić od `T`lub `T` być typem parametru w metodzie `T1`.
 
- Element **ByRef** do pola statycznego, które należy do `T`.

- <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>lub <xref:System.RuntimeMethodHandle> odwołujące się do `T` lub składnika `T`.

- Wystąpienie dowolnego obiektu odbicia, które może być używane pośrednio lub bezpośrednio w celu uzyskania dostępu do obiektu <xref:System.Type>, który reprezentuje `T`. Na przykład obiekt <xref:System.Type> dla `T` można uzyskać z typu tablicy, którego typem elementu jest `T`lub z typu ogólnego, który ma `T` jako argument typu. 

- Metoda `M` na stosie wywołań dowolnego wątku, gdzie `M` jest metodą `T` lub metodą poziomu modułu, która jest zdefiniowana w zestawie.

- Delegat do statycznej metody, która jest zdefiniowana w module zestawu.

Jeśli istnieje tylko jeden element z tej listy tylko dla jednego typu lub jednej metody w zestawie, środowisko uruchomieniowe nie może zwolnić zestawu.

> [!NOTE]
> Środowisko uruchomieniowe nie zwalnia zestawu, dopóki nie zostaną uruchomione finalizatory dla wszystkich elementów na liście.

W celach śledzenia okres istnienia, skonstruowany typ ogólny, taki jak `List<int>` C#(in) lub `List(Of Integer)` (w Visual Basic), który jest tworzony i używany w generacji zestawu kolekcjonowanego, jest uznawany za zdefiniowany w zestawie, który zawiera definicję typu ogólnego lub w zestawie, który zawiera definicję jednego z argumentów typu. Dokładny zestaw, który jest używany jest szczegółami implementacji i może ulec zmianie.
 
## <a name="restrictions-on-collectible-assemblies"></a>Ograniczenia dotyczące zestawów kolekcjonowanych

Do zestawów kolekcjonowanych dotyczą następujące ograniczenia: 

- **Odwołania statyczne**   
  Typy w zwykłym zestawie dynamicznym nie mogą zawierać statycznych odwołań do typów, które są zdefiniowane w zestawie kolekcjonowania. Na przykład, jeśli zdefiniujesz zwykły typ, który dziedziczy z typu w zestawie kolekcjonowanym, zostanie zgłoszony wyjątek <xref:System.NotSupportedException>. Typ w zestawie kolekcjonowania może mieć statyczne odwołania do typu w innym zestawie kolekcjonowanym, ale wydłuży okres istnienia przywoływanego zestawu do okresu istnienia zestawu, do którego się odwołuje.

-   **międzyoperacyjności modelu COM**  
   W obrębie zestawu kolekcjonowanego nie można definiować interfejsów COM, a żadne wystąpienia typów w ramach zestawu kolekcjonowanego nie mogą być konwertowane na obiekty COM. Typ w zestawie kolekcjonowania nie może być obiektem, który jest wywoływany przez COM otokę (CCW) lub otokę wywoływaną przez środowisko uruchomieniowe (RCW). Jednak typy w zestawach kolekcjonowanych mogą korzystać z obiektów, które implementują interfejsy COM.

-   **wywołania platformy**  
   Metody, które mają atrybut <xref:System.Runtime.InteropServices.DllImportAttribute> nie zostaną skompilowane, gdy są zadeklarowane w zestawie kolekcjonowanym. Instrukcji <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> nie można użyć w implementacji typu w zestawie kolekcjonowanym, a takie typy nie mogą być organizowane w kodzie niezarządzanym. Można jednak wywołać kod natywny przy użyciu punktu wejścia zadeklarowanego w niekolekcjonowanym zestawie.
 
- **Kierowanie**   
   Obiektów (w szczególności delegatów), które są zdefiniowane w zestawach kolekcjonowanych nie można zorganizować. Jest to ograniczenie dla wszystkich typów emisji przejściowych.

-   **ładowania zestawu**  
   Emisja odbicia jest jedynym mechanizmem, który jest obsługiwany w przypadku ładowania zestawów kolekcjonowanych. Zestawy, które są ładowane przy użyciu jakiejkolwiek innej formy ładowania zestawu nie mogą zostać zwolnione.
 
- **Obiekty powiązane z kontekstem**    
   Zmienne kontekstowe nie są obsługiwane. Typy w zestawie kolekcjonowania nie mogą poszerzać <xref:System.ContextBoundObject>. Jednak kod w zestawach kolekcjonowanych może korzystać z obiektów powiązanych z kontekstem, które są zdefiniowane w innym miejscu.

-       **danych ze statycznym wątkiem**  
   Zmienne statyczne wątku nie są obsługiwane.

## <a name="see-also"></a>Zobacz także

- [Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)
