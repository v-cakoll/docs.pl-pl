---
title: bindingFailure MDA
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e904d452b9f4a1b172d35984b752c0d97228338
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875085"
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA

`bindingFailure` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy zestaw nie udało się załadować.

## <a name="symptoms"></a>Symptomy

Kod podjął próbę załadowania zestawu przy użyciu statyczne odwołanie lub jednej z metod modułu ładującego, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. Zestaw nie jest załadowany i <xref:System.IO.FileNotFoundException> lub <xref:System.IO.FileLoadException> jest zgłaszany wyjątek.

## <a name="cause"></a>Przyczyna

Niepowodzenie powiązania występuje, gdy środowisko uruchomieniowe nie może załadować zestawu. Niepowodzenie powiązania mogą wynikać z jednej z następujących sytuacji:

- Środowisko uruchomieniowe języka wspólnego (CLR) nie można odnaleźć żądanego zestawu. Istnieje wiele przyczyn, że taka sytuacja może wystąpić, np. zestaw nie jest zainstalowany lub aplikacja nie jest prawidłowo skonfigurowane do znajdowania zestawu.

- Typowy scenariusz problemu to przekazanie typu do innej domeny aplikacji, co wymaga środowiska CLR do załadowania zestawu zawierającego tego typu w domenie aplikacji. Może nie być możliwe dla środowiska uruchomieniowego do załadowania zestawu, jeśli domena aplikacji jest inaczej skonfigurowana od oryginalnego domeny aplikacji. Na przykład, obu domen aplikacji może mieć różne <xref:System.AppDomain.BaseDirectory%2A> wartości właściwości.

- Żądany zestaw jest uszkodzony lub nie jest zestawem.

- Kod próby załadowania zestawu nie ma uprawnienia zabezpieczeń dostępu kodu poprawne ładować zestawy.

- Poświadczenia użytkownika nie są oferowane wymaganych uprawnień do odczytu tego pliku.

## <a name="resolution"></a>Rozwiązanie

Pierwszym krokiem jest ustalenie, dlaczego CLR nie można powiązać żądany zestaw. Istnieje wiele powodów, dlaczego środowisko wykonawcze nie zostały znalezione lub został stanie obciążenia żądany zestaw, takich jak scenariusze opisane w sekcji Przyczyna. Aby wyeliminować przyczynę niepowodzenia powiązania, zaleca się następujące akcje:

- Ustalić przyczynę przy użyciu danych udostępnionych przez `bindingFailure` MDA:

  - Uruchom [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) odczytać dzienniki błędów, generowane przez binder zestawu.

  - Określ, jeśli zestaw znajduje się w lokalizacji, na żądanie. W przypadku właściwości <xref:System.Reflection.Assembly.LoadFrom%2A> i <xref:System.Reflection.Assembly.LoadFile%2A> można łatwo określić metod, żądanej lokalizacji. W przypadku właściwości <xref:System.Reflection.Assembly.Load%2A> metody, która wiąże przy użyciu tożsamości zestawu, musisz sprawdzić dla zestawów, które odpowiadają tej tożsamości w domenie aplikacji <xref:System.AppDomain.BaseDirectory%2A> ścieżka sondy właściwości i globalnej pamięci podręcznej.

- Rozwiąż przyczynę oparte na określenie poprzedniej. Opcje rozpoznawania możliwe są następujące:

  - Zainstaluj żądany zestaw w globalnej pamięci podręcznej zestawów i wywołania. <xref:System.Reflection.Assembly.Load%2A> Metoda można załadować zestawu przez tożsamość.

  - Skopiuj żądany zestaw do katalogu aplikacji i wywołanie <xref:System.Reflection.Assembly.Load%2A> metodę, aby załadować zestaw przez tożsamość.

  - Ponownie skonfiguruj domenę aplikacji, w którym wystąpił błąd powiązania obejmujący ścieżkę zestawu, wprowadzając dowolną zmianę <xref:System.AppDomain.BaseDirectory%2A> właściwości lub dodawanie prywatnych ścieżkach sondowania.

  - Zmiana listy kontroli dostępu do pliku umożliwić zalogowanego użytkownika można odczytać pliku.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe

To zdarzenie MDA nie ma wpływu na środowisko CLR. Informuje jedynie dane o powiązaniu błędów.

## <a name="output"></a>Dane wyjściowe

MDA raporty zestawu, który nie udało się załadować, w tym żądana ścieżka lub nazwa wyświetlana, kontekstu powiązania, domeny aplikacji, w której zażądano obciążenia i przyczynę błędu.

Żądana ścieżka lub nazwa wyświetlana może być pusta, jeśli te dane są niedostępne do środowiska CLR. Jeśli było wywołanie, który uległ awarii <xref:System.Reflection.Assembly.Load%2A> metoda, prawdopodobnie środowisko wykonawcze nie można określić nazwę wyświetlaną dla zestawu.

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Przykład

W poniższym przykładzie kodu pokazano sytuację, która może aktywować to zdarzenie MDA:

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
