---
title: Typy ogólne i odbicie (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 7e35c7d6712323bd7088ad68160da05cdf3a5115
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245781"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Typy ogólne i odbicie (Przewodnik programowania w języku C#)
Ponieważ środowisko uruchomieniowe języka wspólnego (CLR) ma dostęp do informacji o typie ogólny w czasie wykonywania, można użyć odbicia, aby uzyskać informacje na temat typów ogólnych w taki sam sposób jak w przypadku typów innych niż ogólne. Aby uzyskać więcej informacji, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 W [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] kilka nowych elementów członkowskich są dodawane do <xref:System.Type> klasy, aby włączyć informacje środowiska wykonawczego dla typów ogólnych. Zobacz dokumentację na temat tych klas, aby uzyskać więcej informacji na temat korzystania z tych metod i właściwości. <xref:System.Reflection.Emit> Przestrzeń nazw zawiera także nowych elementów członkowskich, które obsługują elementy ogólne. Zobacz [porady: Definiowanie typu ogólnego przy użyciu odbicia emitować](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Aby uzyskać listę niezmiennych warunków dla terminów używanych w odbiciu rodzajowym, zobacz <xref:System.Type.IsGenericType%2A> uwagi dotyczące właściwości.  
  
|Nazwa elementu członkowskiego System.Type|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Zwraca wartość PRAWDA, jeśli typ ogólny.|  
|<xref:System.Type.GetGenericArguments%2A>|Zwraca tablicę `Type` obiekty reprezentujące argumentów typu dostarczony skonstruowanego typu lub typu parametrów w definicji typu ogólnego.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Zwraca podstawową definicję typu ogólnego dla bieżącego typu skonstruowany.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Zwraca tablicę `Type` obiekty reprezentujące ograniczenia bieżącego ogólnego, parametr typu.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Zwraca wartość PRAWDA, jeśli typ, ani żadnego z otaczających typy lub metody zawiera parametry typu, dla których określonych typów nie został podany.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Pobiera kombinacji `GenericParameterAttributes` flagi opisujące specjalnych ograniczeń bieżący ogólny typ parametru.|  
|<xref:System.Type.GenericParameterPosition%2A>|Aby uzyskać `Type` obiekt, który reprezentuje parametr typu, pobiera pozycja parametru typu na liście parametrów typu w definicji typu ogólnego lub definicję metody rodzajowej, zadeklarowany parametr typu.|  
|<xref:System.Type.IsGenericParameter%2A>|Pobiera wartość wskazującą, czy bieżący `Type` reprezentuje parametr typu ogólnego definicji typu lub metody.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Pobiera wartość wskazującą, czy bieżący <xref:System.Type> reprezentuje definicji typu ogólnego, z którego można skonstruować innych typów ogólnych. Zwraca wartość PRAWDA, jeśli typ reprezentuje definicji typu ogólnego.|  
|<xref:System.Type.DeclaringMethod%2A>|Zwraca metody rodzajowej, zdefiniowanego bieżący ogólny, parametr typu, lub wartość null, jeśli parametr typu nie został zdefiniowany przez metody rodzajowej.|  
|<xref:System.Type.MakeGenericType%2A>|Zastępuje elementy tablicy typów jako parametrów typu w bieżącej definicji typu ogólnego, a następnie zwraca <xref:System.Type> obiekt reprezentujący wynikowy tworzony typu.|  
  
 Ponadto członkowie <xref:System.Reflection.MethodInfo> klasy włączyć informacje czasu wykonywania dla metod ogólnych. Zobacz <xref:System.Reflection.MethodBase.IsGenericMethod%2A> uwagi dotyczące właściwości, aby uzyskać listę niezmiennych warunków dla terminów używanych na zastanowienie się nad metod ogólnych.  
  
|System.Reflection.MemberInfo Member Name|Opis|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Zwraca wartość PRAWDA, jeśli metoda jest ogólna.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Zwraca tablicę obiektów typu, reprezentujących argumenty typu metody ogólnej skonstruowany lub parametrów typu w definicji metody rodzajowej.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Zwraca podstawową definicję metody ogólnej przy użyciu bieżącej metody skonstruowany.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Zwraca wartość PRAWDA, jeśli metoda albo jej otaczającej typy zawierają wszystkie parametry typu, dla których nie zostały dostarczone określonych typów.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Zwraca wartość true, jeśli bieżący <xref:System.Reflection.MethodInfo> reprezentuje definicję metody rodzajowej.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Zastępuje elementy tablicy typów dla parametrów typu bieżącej definicji metody rodzajowej, a następnie zwraca <xref:System.Reflection.MethodInfo> obiekt reprezentujący wynikowy tworzony metody.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
 [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [Typy ogólne](~/docs/standard/generics/index.md)
