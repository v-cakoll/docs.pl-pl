---
title: "Typy ogólne i odbicie (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc2363eea7d5c601fc73f5f9eb14b4b07ad14cb8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-reflection-c-programming-guide"></a>Typy ogólne i odbicie (Przewodnik programowania w języku C#)
Ponieważ środowisko uruchomieniowe języka wspólnego (CLR) ma dostęp do informacji typu ogólnego w czasie wykonywania, można użyć odbicia uzyskanie informacji na temat typów ogólnych w taki sam sposób jak w przypadku typów nierodzajową. Aby uzyskać więcej informacji, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 W [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] kilka nowych elementów członkowskich są dodawane do <xref:System.Type> klasę, aby włączyć informacje czasu wykonywania dla typów ogólnych. W dokumentacji tych klas, aby uzyskać więcej informacji na temat korzystania z tych metod i właściwości. <xref:System.Reflection.Emit> Przestrzeń nazw zawiera również nowe elementy członkowskie, które obsługuje elementów ogólnych. Zobacz [porady: Definiowanie typu ogólnego z odbiciem Emituj](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Lista niezmiennej warunki terminów używanych w ogólnym odbicia, zobacz <xref:System.Type.IsGenericType%2A> właściwości uwagi.  
  
|Nazwa elementu członkowskiego System.Type|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Zwraca wartość PRAWDA, jeśli typ jest rodzajowy.|  
|<xref:System.Type.GetGenericArguments%2A>|Zwraca tablicę `Type` obiektów, które reprezentują argumentów typu dostarczona do skonstruowanego typu lub typ parametrów definicji typu ogólnego.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Zwraca podstawowej definicji typu ogólnego dla bieżącego typu skonstruowane.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Zwraca tablicę `Type` obiekty reprezentujące ograniczenia dotyczące bieżącego ogólnego typu parametru.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Zwraca wartość PRAWDA, jeśli typ lub dowolny z jego otaczającego typach lub metodach zawierają parametrów typu, dla których określonych typów nie został podany.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Pobiera kombinację `GenericParameterAttributes` flagi opisujące ograniczeń specjalnych z bieżącym ogólnego typu parametru.|  
|<xref:System.Type.GenericParameterPosition%2A>|Aby uzyskać `Type` pozycja parametru typu na liście parametrów typu w definicji typu ogólnego lub ogólną definicją metody zadeklarowany parametr typu pobiera obiekt, który reprezentuje parametr typu.|  
|<xref:System.Type.IsGenericParameter%2A>|Pobiera wartość wskazującą, czy bieżący `Type` reprezentuje parametr typu ogólnego definicji typu lub metody.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Pobiera wartość wskazującą, czy bieżący <xref:System.Type> reprezentuje definicji typu ogólnego, z którego można skonstruować innych typów ogólnych. Zwraca wartość PRAWDA, jeśli typ reprezentuje definicji typu ogólnego.|  
|<xref:System.Type.DeclaringMethod%2A>|Zwraca metody ogólnej zdefiniowanego bieżący ogólny parametr typu, lub wartość null, jeśli parametr typu nie został zdefiniowany przez metody rodzajowej.|  
|<xref:System.Type.MakeGenericType%2A>|Zastępuje elementy tablicą typów parametrów typu bieżącej definicji typu ogólnego i zwraca <xref:System.Type> obiekt reprezentujący powstałe w ten sposób skonstruować typu.|  
  
 Ponadto nowe elementy członkowskie są dodawane do <xref:System.Reflection.MethodInfo> klasę, aby włączyć informacje czasu wykonywania dla metod generycznych. Zobacz <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> uwagi właściwości listę niezmiennej warunki terminów używanych w celu odzwierciedlenia na metody ogólne.  
  
|Nazwa elementu członkowskiego System.Reflection.MemberInfo|Opis|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|Zwraca wartość PRAWDA, jeśli metody jest rodzajowy.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Zwraca tablicę obiektów typu, które reprezentują argumentów typu skonstruowane metody ogólnej lub parametrów typu definicję metody rodzajowej.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Zwraca podstawowej ogólną definicją metody dla bieżącej metody skonstruowane.|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|Zwraca wartość PRAWDA, jeśli metoda lub jej otaczającego typy zawierać żadnych parametrów typu, dla których nie podano określonych typów.|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|Zwraca wartość true, jeśli bieżący <xref:System.Reflection.MethodInfo> reprezentuje definicję metody rodzajowej.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Zastępuje elementy tablicą typów parametrów typu bieżącej definicji metody rodzajowej i zwraca <xref:System.Reflection.MethodInfo> obiekt reprezentujący powstałe w ten sposób skonstruowany — metoda.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
 [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [Typy ogólne](~/docs/standard/generics/index.md)
