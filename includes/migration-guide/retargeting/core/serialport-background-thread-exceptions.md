---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614747"
---
### <a name="serialport-background-thread-exceptions"></a>Wyjątki wątku w tle klasy SerialPort

#### <a name="details"></a>Szczegóły

Wątki w tle utworzone za pomocą <xref:System.IO.Ports.SerialPort> strumieni nie przerywają procesu, gdy są zgłaszane wyjątki systemu operacyjnego. <br/>W aplikacjach, które są przeznaczone dla .NET Framework 4,7 i wcześniejszych wersji, proces zostaje zakończony, gdy w wątku w tle utworzonym za pomocą strumienia zostanie zgłoszony wyjątek systemu operacyjnego <xref:System.IO.Ports.SerialPort> . <br/>W aplikacjach przeznaczonych dla .NET Framework 4.7.1 lub nowszej wersji wątki w tle czekają na zdarzenia systemu operacyjnego związane z aktywnym portem szeregowym i mogą ulec awarii w niektórych przypadkach, takich jak nagłe usunięcie portu szeregowego.

#### <a name="suggestion"></a>Sugestia

W przypadku aplikacji przeznaczonych dla .NET Framework 4.7.1 można zrezygnować z obsługi wyjątków, jeśli nie jest to pożądane, dodając następujący element do `<runtime>` sekcji `app.config` pliku:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

W przypadku aplikacji przeznaczonych dla wcześniejszych wersji .NET Framework ale uruchamianych na .NET Framework 4.7.1 lub nowszych można zrezygnować z obsługi wyjątków, dodając następujący element do `<runtime>` sekcji `app.config` pliku:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
