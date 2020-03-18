---
title: Rozwiązywanie załadowań zestawów
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d6314fae266505fbb4410aaaa351973070ab3811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156442"
---
# <a name="resolve-assembly-loads"></a>Rozwiązywanie załadowań zestawów
.NET udostępnia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie dla aplikacji, które wymagają większej kontroli nad ładowaniem zestawu. Obsługując to zdarzenie, aplikacja może załadować zestaw do kontekstu obciążenia spoza normalnych ścieżek sondowania, wybrać, która z kilku wersji zestawu do załadowania, emitują zestaw dynamiczny i zwracają go i tak dalej. W tym temacie przedstawiono <xref:System.AppDomain.AssemblyResolve> wskazówki dotyczące obsługi zdarzenia.  
  
> [!NOTE]
> Do rozpoznawania obciążeń złożenia w kontekście <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> tylko do odbicia, należy użyć zdarzenia zamiast tego.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak działa zdarzenie AssemblyResolve  
 Podczas rejestrowania programu <xref:System.AppDomain.AssemblyResolve> obsługi dla zdarzenia, program obsługi jest wywoływany za każdym razem, gdy czas wykonywania nie powiedzie się powiązać z zestawem według nazwy. Na przykład wywołanie następujących metod z kodu <xref:System.AppDomain.AssemblyResolve> użytkownika może spowodować zdarzenie, które mają być wywoływane:  
  
- Przeciążenie <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub przeciążenie metody, którego pierwszy argument jest ciągiem reprezentującym nazwę wyświetlaną zestawu <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> do załadowania (czyli ciąg zwrócony przez właściwość).  
  
- Przeciążenie <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub przeciążenie metody, którego pierwszy argument jest obiektem identyfikującym <xref:System.Reflection.AssemblyName> zestaw do załadowania.  
  
- Przeciążenie <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody.  
  
- Przeciążenie <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> metoda, która tworzy obiekt w innej domenie aplikacji.  
  
### <a name="what-the-event-handler-does"></a>Co robi program obsługi zdarzeń  
 Program obsługi <xref:System.AppDomain.AssemblyResolve> zdarzenia odbiera nazwę wyświetlana zestawu, który <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> ma zostać załadowany we właściwości. Jeśli program obsługi nie rozpoznaje nazwy `null` zestawu, zwraca `Nothing` (C#), `nullptr` (Visual Basic) lub (Visual C++).  
  
 Jeśli program obsługi rozpoznaje nazwę zestawu, można załadować i zwrócić zestaw, który spełnia żądanie. Na poniższej liście opisano niektóre przykładowe scenariusze.  
  
- Jeśli program obsługi zna lokalizację wersji zestawu, można załadować <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> zestawu przy użyciu lub metody i może zwrócić załadowany zestaw, jeśli zakończy się pomyślnie.  
  
- Jeśli program obsługi ma dostęp do bazy danych zestawów przechowywanych jako tablice bajtów, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> można załadować tablicy bajtów przy użyciu jednego z przeciążeń metody, które przyjmują tablicy bajtów.  
  
- Program obsługi może wygenerować zestaw dynamiczny i zwrócić go.  
  
> [!NOTE]
> Program obsługi musi załadować zestaw do kontekstu obciążenia z kontekstu, do kontekstu obciążenia lub bez kontekstu. Jeśli program obsługi ładuje zestaw do kontekstu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> tylko <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> do odbicia przy użyciu <xref:System.AppDomain.AssemblyResolve> lub metody, próba obciążenia, który wywołał zdarzenie nie powiedzie się.  
  
 Jest odpowiedzialny za program obsługi zdarzeń, aby zwrócić odpowiedni zestaw. Program obsługi można przeanalizować nazwę wyświetlaną żądanego <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> zestawu, przekazując wartość właściwości do <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> konstruktora. Począwszy od .NET Framework 4, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> program obsługi można użyć właściwości, aby ustalić, czy bieżące żądanie jest zależność innego zestawu. Te informacje mogą pomóc zidentyfikować zestaw, który spełni zależność.  
  
 Program obsługi zdarzeń może zwrócić inną wersję zestawu niż żądana wersja.  
  
 W większości przypadków zestawu, który jest zwracany przez program obsługi pojawia się w kontekście obciążenia, niezależnie od kontekstu obsługi ładuje go do. Na przykład jeśli program <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> obsługi używa metody do ładowania zestawu do kontekstu obciążenia z, zestaw pojawia się w kontekście obciążenia, gdy program obsługi zwraca go. Jednak w następującym przypadku zestaw pojawia się bez kontekstu, gdy program obsługi zwraca go:  
  
- Program obsługi ładuje zestaw bez kontekstu.  
  
- Właściwość <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> nie jest null.  
  
- Żądający zestaw (czyli zestaw, który jest zwracany przez <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> właściwość) został załadowany bez kontekstu.  
  
 Aby uzyskać informacje o <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> kontekstach, zobacz przeciążenie metody.  
  
 Wiele wersji tego samego zestawu można załadować do tej samej domeny aplikacji. Ta praktyka nie jest zalecana, ponieważ może prowadzić do problemów z przypisaniem typu. Zobacz [Najważniejsze wskazówki dotyczące ładowania zestawu](../../framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Czego program obsługi zdarzeń nie powinien robić  
Podstawową regułą <xref:System.AppDomain.AssemblyResolve> obsługi zdarzenia jest, że nie należy próbować zwrócić zestawu, który nie rozpoznaje. Podczas pisania programu obsługi, należy wiedzieć, które zestawy mogą spowodować zdarzenie, które mają być wywoływane. Program obsługi powinien zwracać null dla innych zestawów.  

> [!IMPORTANT]
> Począwszy od .NET Framework <xref:System.AppDomain.AssemblyResolve> 4, zdarzenie jest wywoływane dla zestawów satelickich. Ta zmiana ma wpływ na program obsługi zdarzeń, który został napisany dla starszej wersji programu .NET Framework, jeśli program obsługi próbuje rozwiązać wszystkie żądania ładowania zestawu. Programy obsługi zdarzeń, które ignorują zestawy, których nie rozpoznają, nie mają wpływu na tę zmianę: zwracają wartość null i przestrzegane są normalne mechanizmy rezerwowe.  

Podczas ładowania zestawu, program obsługi zdarzeń <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> może używać żadnych <xref:System.AppDomain.AssemblyResolve> przeciążeń lub metody, które mogą spowodować zdarzenie, które mają być wywoływane cyklicznie, ponieważ może to prowadzić do przepełnienia stosu. (Zobacz listę podanych wcześniej w tym temacie). Dzieje się tak, nawet jeśli podasz obsługę wyjątków dla żądania obciążenia, ponieważ nie wyjątek, dopóki nie zostaną zwrócone wszystkie programy obsługi zdarzeń. W związku z tym następujący kod `MyAssembly` powoduje przepełnienie stosu, jeśli nie zostanie znaleziony:  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);
        return Assembly.Load(e.Name);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System.Reflection

Class BadExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

## <a name="see-also"></a>Zobacz też

- [Najważniejsze wskazówki dotyczące ładowania zestawu](../../framework/deployment/best-practices-for-assembly-loading.md)
- [Korzystanie z domen aplikacji](../../framework/app-domains/use.md)
