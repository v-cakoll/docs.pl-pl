---
title: 'Porady: definiowanie i wykonywanie metod dynamicznych'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c2b3f1707aab1f83d8f8c6a06bc2efa909134d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Porady: definiowanie i wykonywanie metod dynamicznych
Poniższe procedury pokazują, jak definiowanie i wykonywanie prosta metoda dynamiczne i dynamiczna metoda powiązany z wystąpieniem klasy. Więcej informacji na temat metod dynamicznych, zobacz <xref:System.Reflection.Emit.DynamicMethod> klasy i [emisji dynamicznego metody scenariuszami odbicia](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Aby zdefiniować i wykonania metody dynamiczne  
  
1.  Należy zadeklarować typ delegata można wykonać metody. Należy rozważyć użycie do minimalizacji liczby typów delegatów, które należy zadeklarować to delegat generyczny. Poniższy kod deklaruje delegata dwa typy, które mogłyby zostać użyte do `SquareIt` — metoda i jeden z nich jest rodzajowy.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  Utwórz tablicę, która określa typ parametru metody dynamicznej. W tym przykładzie jest tylko parametr `int` (`Integer` w języku Visual Basic), przez co tablica zawiera tylko jeden element.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  Utwórz <xref:System.Reflection.Emit.DynamicMethod>. W tym przykładzie metodę o nazwie `SquareIt`.  
  
    > [!NOTE]
    >  Nie jest konieczne, nadaj nazwę metody dynamiczne i nie można wywołać według nazwy. Wiele metod dynamicznych może mieć takiej samej nazwie. Jednak nazwa jest wyświetlana w stosy wywołań i mogą być przydatne do debugowania.  
  
     Typ wartości zwracanej jest określony jako `long`. Metoda jest skojarzony z moduł, który zawiera `Example` klasy, która zawiera przykładowy kod. Każdy moduł załadować może być określony. Działa dynamiczna metoda jak poziom modułu `static` — metoda (`Shared` w języku Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  Emituj treści metody. W tym przykładzie <xref:System.Reflection.Emit.ILGenerator> obiekt jest używany do wysyłania język pośredni firmy Microsoft (MSIL). Alternatywnie <xref:System.Reflection.Emit.DynamicILInfo> obiektu można w połączeniu z generatory kodu niezarządzanego Emituj treść metody <xref:System.Reflection.Emit.DynamicMethod>.  
  
     MSIL w tym przykładzie ładuje argumentu, który jest `int`, na stosie, konwertuje go do `long`, duplikaty `long`i mnoży dwie liczby. Wynik kwadratów pozostawione na stosie, a metoda ma robić, jest zwracany.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  Utwórz wystąpienie obiektu delegowanego (deklaracja w kroku 1) reprezentuje przez wywołanie metody dynamicznej <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody. Tworzenie obiektu delegowanego ukończeniu metody i wszelkie dodatkowe próbuje zmienić metodę — na przykład dodać więcej MSIL — są ignorowane. Poniższy kod tworzy delegata i wywołuje, przy użyciu to delegat generyczny.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Aby zdefiniować i wykonać dynamicznej metodę, która jest powiązana z obiektem  
  
1.  Należy zadeklarować typ delegata można wykonać metody. Należy rozważyć użycie do minimalizacji liczby typów delegatów, które należy zadeklarować to delegat generyczny. Poniższy kod deklaruje typ Delegat ogólny, który może służyć do wykonywania dowolnej metody z jednym parametrem i zwracanej wartości, lub metody z dwóch parametrów i wartości zwracanej, jeśli delegat jest powiązana z obiektem.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  Utwórz tablicę, która określa typ parametru metody dynamicznej. W przypadku delegata reprezentującego metodę powiązać obiektu, pierwszy parametr musi być zgodna z typu obiektu delegowanego jest powiązany z. W tym przykładzie są dwa parametry typu `Example` i typ `int` (`Integer` w języku Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  Utwórz <xref:System.Reflection.Emit.DynamicMethod>. W tym przykładzie metoda nie ma nazwy. Typ wartości zwracanej jest określony jako `int` (`Integer` w języku Visual Basic). Metoda ma dostęp do członków prywatnych i chronionych `Example` klasy.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  Emituj treści metody. W tym przykładzie <xref:System.Reflection.Emit.ILGenerator> obiekt jest używany do wysyłania język pośredni firmy Microsoft (MSIL). Alternatywnie <xref:System.Reflection.Emit.DynamicILInfo> obiektu można w połączeniu z generatory kodu niezarządzanego Emituj treść metody <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Pierwszy argument, który jest wystąpieniem ładuje MSIL w tym przykładzie z `Example` klasy i używa go do załadowania wartości pola prywatne wystąpienia typu `int`. Drugi argument jest załadowany, i są mnożone dwóch liczb. Jeśli wynik jest większy niż `int`, wartość zostanie obcięta i najbardziej znaczących bitów zostaną odrzucone. Metoda zwraca z wartością zwracaną na stosie.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  Utwórz wystąpienie obiektu delegowanego (deklaracja w kroku 1) reprezentuje przez wywołanie metody dynamicznej <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> przeciążenie metody. Tworzenie obiektu delegowanego ukończeniu metody i wszelkie dodatkowe próbuje zmienić metodę — na przykład dodać więcej MSIL — są ignorowane.  
  
    > [!NOTE]
    >  Możesz wywołać <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody kilka razy do tworzenia delegatów powiązana z innymi wystąpieniami typu docelowego.  
  
     Poniższy kod wiąże metody nowe wystąpienie klasy `Example` klasy, których pole prywatne testu ma ustawioną wartość 42. Oznacza to, zawsze jest delegat wywoływany wystąpienie `Example` jest przekazywany do pierwszego parametru metody.  
  
     Delegat `OneParameter` jest używany, ponieważ pierwszy parametr metody zawsze otrzymuje wystąpienie `Example`. Po wywołaniu delegat drugi parametr jest wymagany.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano prostą metodę dynamicznego i dynamiczna metoda powiązany z wystąpieniem klasy.  
  
 Prosta metoda dynamiczne przyjmuje jeden argument, 32-bitową liczbę całkowitą i zwraca kwadrat 64-bitowych tej liczby całkowitej. Delegat ogólny służy do wywoływania metody.  
  
 Druga metoda dynamiczne ma dwa parametry typu `Example` i typ `int` (`Integer` w języku Visual Basic). Podczas tworzenia metody dynamicznej jest on powiązany z wystąpieniem `Example`, przy użyciu Delegat ogólny, który ma jeden argument typu `int`. Delegat nie ma argumentu typu `Example` ponieważ pierwszy parametr metody otrzymuje zawsze powiązane wystąpienie `Example`. Jeśli delegat jest wywoływany, tylko `int` argumentu. Pole prywatne uzyskuje dostęp do tej metody dynamicznej `Example` klasy i zwraca iloczyn pole prywatne i `int` argumentu.  
  
 Przykładowy kod definiuje delegatów, które mogą służyć do wykonywania metody.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod C# `using` instrukcje (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawów dodatkowe są wymagane.  
  
-   Kompilowanie kodu w wierszu polecenia przy użyciu csc.exe, vbc.exe lub cl.exe. Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie Projekt aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [Emituj za pomocą odbicia](http://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Emisja odbicia scenariuszy dynamicznej — metoda](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
