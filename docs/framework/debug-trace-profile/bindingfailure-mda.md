---
title: bindingFailure MDA
description: Przeczytaj o bindingFailure Managed Debug Assistant (MDA), który jest uaktywniany w przypadku niepowodzenia ładowania zestawu w programie .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: 98c7947c7e5d2a1f0af8c26744d3b292ed8cb4c4
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415631"
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA

`bindingFailure`Asystent debugowania zarządzanego (MDA) jest uaktywniany w przypadku niepowodzenia ładowania zestawu.

## <a name="symptoms"></a>Objawy

Kod podjął próbę załadowania zestawu przy użyciu statycznego odwołania lub jednej z metod Loader, takich jak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> . Zestaw nie został załadowany i <xref:System.IO.FileNotFoundException> <xref:System.IO.FileLoadException> zostanie zgłoszony wyjątek lub.

## <a name="cause"></a>Przyczyna

Błąd powiązania występuje, gdy środowisko uruchomieniowe nie może załadować zestawu. Błąd powiązania może wynikać z jednej z następujących sytuacji:

- Środowisko uruchomieniowe języka wspólnego (CLR) nie może znaleźć żądanego zestawu. Istnieje wiele powodów, na przykład nieinstalacja zestawu lub aplikacja, która nie jest poprawnie skonfigurowana do znajdowania zestawu.

- Typowy scenariusz problemu przekazuje typ do innej domeny aplikacji, co wymaga, aby środowisko CLR ładowało zestaw zawierający ten typ w innej domenie aplikacji. Ładowanie zestawu przez środowisko uruchomieniowe może nie być możliwe, jeśli inna domena aplikacji jest skonfigurowana inaczej niż oryginalna domena aplikacji. Na przykład dwie domeny aplikacji mogą mieć różne <xref:System.AppDomain.BaseDirectory%2A> wartości właściwości.

- Żądany zestaw jest uszkodzony lub nie jest zestawem.

- Kod próbujący załadować zestaw nie ma poprawnych uprawnień dostępu kodu do ładowania zestawów.

- Poświadczenia użytkownika nie zapewniają wymaganych uprawnień do odczytu pliku.

## <a name="resolution"></a>Rozwiązanie

Pierwszym krokiem jest określenie, dlaczego nie można powiązać środowiska CLR z żądanym zestawem. Istnieje wiele powodów, dla których środowisko wykonawcze mogło nie zostać odnalezione lub można załadować żądany zestaw, na przykład scenariusze wymienione w sekcji Przyczyna. Aby wyeliminować przyczynę niepowodzenia powiązania, zaleca się wykonanie następujących czynności:

- Ustal przyczynę przy użyciu danych dostarczonych przez `bindingFailure` zdarzenie MDA:

  - Uruchom [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) , aby odczytać dzienniki błędów generowane przez spinacz zestawu.

  - Ustal, czy zestaw znajduje się w lokalizacji, w której zażądano. W przypadku <xref:System.Reflection.Assembly.LoadFrom%2A> <xref:System.Reflection.Assembly.LoadFile%2A> metod i można łatwo określić żądaną lokalizację. W przypadku <xref:System.Reflection.Assembly.Load%2A> metody, która wiąże się przy użyciu tożsamości zestawu, należy wyszukać zestawy, które pasują do tej tożsamości w <xref:System.AppDomain.BaseDirectory%2A> ścieżce sondy właściwości domeny aplikacji i globalnej pamięci podręcznej zestawów.

- Rozwiąż przyczynę w oparciu o poprzednie oznaczenie. Możliwe opcje rozpoznawania są następujące:

  - Zainstaluj żądany zestaw w globalnej pamięci podręcznej zestawów i Wywołaj. <xref:System.Reflection.Assembly.Load%2A>Metoda ładowania zestawu według tożsamości.

  - Skopiuj żądany zestaw do katalogu aplikacji i Wywołaj metodę, <xref:System.Reflection.Assembly.Load%2A> Aby załadować zestaw według tożsamości.

  - Skonfiguruj ponownie domenę aplikacji, w której wystąpił błąd powiązania w celu uwzględnienia ścieżki zestawu przez zmianę <xref:System.AppDomain.BaseDirectory%2A> właściwości lub dodanie prywatnych ścieżek do sondowania.

  - Zmień listę kontroli dostępu dla pliku, aby umożliwić zalogowanemu użytkownikowi odczytywanie pliku.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe

To zdarzenie MDA nie ma wpływu na środowisko CLR. Raportuje tylko dane dotyczące niepowodzeń powiązań.

## <a name="output"></a>Dane wyjściowe

Raport MDA zgłasza zestaw, którego nie udało się załadować, w tym żądaną ścieżkę i/lub nazwę wyświetlaną, kontekst powiązania, domenę aplikacji, w której zażądano obciążenia, oraz przyczynę niepowodzenia.

Nazwa wyświetlana lub żądana ścieżka może być pusta, jeśli te dane nie były dostępne dla środowiska CLR. Jeśli wywołanie, które zakończyło się niepowodzeniem <xref:System.Reflection.Assembly.Load%2A> , prawdopodobnie środowisko uruchomieniowe nie mogło określić nazwy wyświetlanej zestawu.

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje sytuację, w której można aktywować to MDA:

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

## <a name="see-also"></a>Zobacz też

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
