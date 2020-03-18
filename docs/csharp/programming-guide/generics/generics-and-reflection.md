---
title: Rodzajowe i odbicie - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 4893bf5ebe73988bb6535cc2a85591ff0dde6ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712172"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Typy ogólne i odbicie (Przewodnik programowania w języku C#)
Ponieważ common language runtime (CLR) ma dostęp do ogólnych informacji o typie w czasie wykonywania, można użyć odbicia, aby uzyskać informacje o typach ogólnych w taki sam sposób, jak dla typów nieogólnych. Aby uzyskać więcej informacji, zobacz [Ogólne w czasie wykonywania](./generics-in-the-run-time.md).  
  
 W .NET Framework 2.0 kilka nowych elementów <xref:System.Type> członkowskich są dodawane do klasy, aby włączyć informacje w czasie wykonywania dla typów ogólnych. Zobacz dokumentację tych klas, aby uzyskać więcej informacji na temat używania tych metod i właściwości. Obszar <xref:System.Reflection.Emit> nazw zawiera również nowe elementy członkowskie, które obsługują leki ogólne. Zobacz [jak: Definiowanie typu ogólnego z odbiciem Emit](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Aby uzyskać listę niezmiennych warunków dla terminów używanych w ogólnej refleksji, zobacz uwagi <xref:System.Type.IsGenericType%2A> właściwości.  
  
|Nazwa elementu członkowskiego System.Type|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Zwraca wartość true, jeśli typ jest ogólny.|  
|<xref:System.Type.GetGenericArguments%2A>|Zwraca tablicę `Type` obiektów, które reprezentują argumenty typu dostarczone dla typu konstruowanego lub parametry typu definicji typu ogólnego.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Zwraca podstawową definicję typu ogólnego dla bieżącego typu konstruowanego.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Zwraca tablicę `Type` obiektów, które reprezentują ograniczenia bieżącego parametru typu ogólnego.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Zwraca wartość true, jeśli typ lub którykolwiek z jego otaczających typów lub metod zawiera parametry typu, dla których nie podano określonych typów.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Pobiera kombinację `GenericParameterAttributes` flag, które opisują specjalne ograniczenia bieżącego parametru typu ogólnego.|  
|<xref:System.Type.GenericParameterPosition%2A>|Dla `Type` obiektu, który reprezentuje parametr typu, pobiera pozycję parametru typu na liście parametrów typu definicji typu ogólnego lub definicji metody ogólnej, która zadeklarowała parametr typu.|  
|<xref:System.Type.IsGenericParameter%2A>|Pobiera wartość, która wskazuje, czy bieżący `Type` reprezentuje parametr typu typu ogólnego lub definicji metody.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Pobiera wartość, która wskazuje, czy bieżący <xref:System.Type> reprezentuje definicji typu ogólnego, z którego można skonstruować inne typy ogólne. Zwraca wartość true, jeśli typ reprezentuje definicję typu ogólnego.|  
|<xref:System.Type.DeclaringMethod%2A>|Zwraca metodę ogólną, która zdefiniowała bieżący parametr typu ogólnego, lub null, jeśli parametr type nie został zdefiniowany przez metodę rodzajową.|  
|<xref:System.Type.MakeGenericType%2A>|Zastępuje elementy tablicy typów dla parametrów typu bieżącej definicji typu ogólnego <xref:System.Type> i zwraca obiekt reprezentujący wynikowy typ konstruowany.|  
  
 Ponadto elementy członkowskie <xref:System.Reflection.MethodInfo> klasy włączyć informacje w czasie wykonywania dla metod ogólnych. Zobacz <xref:System.Reflection.MethodBase.IsGenericMethod%2A> uwagi właściwości listę niezmiennych warunków dla terminów używanych do refleksji na temat metod ogólnych.  
  
|Nazwa członka System.Reflection.MemberInfo|Opis|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Zwraca wartość true, jeśli metoda jest ogólna.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Zwraca tablicę Type obiektów, które reprezentują argumenty typu skonstruowanej metody ogólnej lub parametry typu definicji metody ogólnej.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Zwraca podstawową definicję metody ogólnej dla bieżącej metody konstruowanej.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Zwraca wartość true, jeśli metoda lub którykolwiek z jej otaczających typów zawiera wszelkie parametry typu, dla których nie podano określonych typów.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Zwraca wartość true, jeśli bieżący <xref:System.Reflection.MethodInfo> reprezentuje definicję metody ogólnej.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Zastępuje elementy tablicy typów dla parametrów typu bieżącej definicji metody ogólnej <xref:System.Reflection.MethodInfo> i zwraca obiekt reprezentujący wynikową metodę konstruowaną.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Typy ogólne](./index.md)
- [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Typy ogólne](../../../standard/generics/index.md)
