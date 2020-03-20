---
title: 'Łagodzenie: Niestandardowe implementacje IMessageFilter.PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400121"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Łagodzenie: Niestandardowe implementacje IMessageFilter.PreFilterMessage

W aplikacjach Windows Forms, które są przeznaczone dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1, implementacja niestandardowa <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> może bezpiecznie filtrować wiadomości, gdy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana, jeśli <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacja:

- Czy jedna lub obie z następujących czynności:

  - Dodaje filtr wiadomości, <xref:System.Windows.Forms.Application.AddMessageFilter%2A> wywołując metodę.

  - Usuwa filtr wiadomości, wywołując <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metodę. Metoda.

- **I** pompuje wiadomości, <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> wywołując metodę.

## <a name="impact"></a>Wpływ

Ta zmiana dotyczy tylko aplikacji Windows Forms, które są przeznaczone dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1.

W przypadku aplikacji Windows Forms przeznaczonych dla poprzednich wersji programu .NET Framework <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> takie implementacje w niektórych przypadkach zgłaszają wyjątek, <xref:System.IndexOutOfRangeException> gdy metoda jest wywoływana

## <a name="mitigation"></a>Środki zaradcze

Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla programu .NET Framework 4.6.1 lub nowszej wersji mogą zrezygnować z niej, dodając następujące ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Ponadto aplikacje przeznaczone dla poprzednich wersji programu .NET Framework, ale uruchomione w ramach programu .NET Framework 4.6.1 lub nowszej wersji, mogą zdecydować się na to zachowanie, dodając następujące ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
