---
title: 'Instrukcje: Odbieranie powiadomień o wyjątkach pierwszej szansy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ef9d90f82abd15de05967262b6e6a4c3a6b842b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164895"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Instrukcje: Odbieranie powiadomień o wyjątkach pierwszej szansy
<xref:System.AppDomain.FirstChanceException> Zdarzenia <xref:System.AppDomain> klasa umożliwia otrzymywanie powiadomień, który jest zwracany wyjątek, przed języka wspólnego środowiska uruchomieniowego została rozpoczęta, wyszukując obsługi wyjątków.

 Zdarzenie jest wywoływane na poziomie domeny aplikacji. Wątek wykonywania mogą przejść przez wiele domen aplikacji, więc wyjątek, który jest nieobsługiwany w jednej domenie aplikacji może być obsługiwane w innej domenie aplikacji. Powiadomienie występuje w każdej domenie aplikacji, która została dodana procedura obsługi zdarzeń, dopóki nie obsługuje wyjątek, domeny aplikacji.

 Procedury składowane i przykłady w niniejszym artykule pokazano, jak otrzymywać powiadomienia o wyjątkach pierwszej szansy w prosty program, który ma jedną domenę aplikacji, a w domenie aplikacji, którą tworzysz.

 Na przykład bardziej złożone, która obejmuje kilka domen aplikacji, zobacz przykład <xref:System.AppDomain.FirstChanceException> zdarzeń.

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Odbieranie powiadomień o wyjątkach pierwszej szansy w domyślnej domeny aplikacji
 W poniższej procedurze punkt wejścia dla aplikacji, `Main()` metoda, jest uruchamiana w domyślnej domeny aplikacji.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>Aby zademonstrować powiadomień o wyjątkach pierwszej szansy w domyślnej domeny aplikacji

1.  Definiowanie zdarzenia obsługi dla <xref:System.AppDomain.FirstChanceException> zdarzenie, przy użyciu wyrażenia lambda funkcji i dołącz je do zdarzenia. W tym przykładzie program obsługi zdarzeń Drukuje nazwę domeny aplikacji, w którym zdarzenie został obsłużony i wyjątków <xref:System.Exception.Message%2A> właściwości.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2.  Zgłoszenie wyjątku i przechwytywać je. Zanim środowisko uruchomieniowe lokalizuje obsługi wyjątków <xref:System.AppDomain.FirstChanceException> zdarzenie jest zgłaszane i zostanie wyświetlony komunikat. Ten komunikat występuje komunikat, który jest wyświetlany przez program obsługi wyjątków.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3.  Zgłoś wyjątek, ale nie Przechwytuj. Zanim środowisko uruchomieniowe szuka obsługi wyjątków <xref:System.AppDomain.FirstChanceException> zdarzenie jest zgłaszane i zostanie wyświetlony komunikat. Jest nie obsługi wyjątków, dlatego zakończenia aplikacji.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     Kod, który jest wyświetlany w pierwszych trzech kroków tej procedury formularzy aplikacji konsoli ukończone. Dane wyjściowe z aplikacji różni się w zależności od nazwy pliku .exe, ponieważ nazwa domyślnej domeny aplikacji składa się z nazwę i rozszerzenie pliku .exe. Zobacz następujące przykładowe dane wyjściowe.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Odbieranie powiadomień o wyjątkach pierwszej szansy w innej domenie aplikacji
 Jeśli program zawiera więcej niż jedną domenę aplikacji, wybierz pozycję domen aplikacji, otrzymywać powiadomienia.

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Aby otrzymywać powiadomienia o wyjątkach pierwszej szansy w domenie aplikacji, którą tworzysz

1.  Definiowanie zdarzenia obsługi dla <xref:System.AppDomain.FirstChanceException> zdarzeń. W tym przykładzie użyto `static` — metoda (`Shared` w języku Visual Basic), drukuje nazwę domeny aplikacji, w którym zdarzenie został obsłużony i wyjątków <xref:System.Exception.Message%2A> właściwości.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2.  Tworzenie domeny aplikacji i dodaj procedurę obsługi zdarzeń do <xref:System.AppDomain.FirstChanceException> zdarzenia dla tej domeny aplikacji. W tym przykładzie domena aplikacji o nazwie `AD1`.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     W ten sam sposób, może obsługiwać to zdarzenie w domyślnej domeny aplikacji. Użyj `static` (`Shared` w języku Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> właściwość `Main()` można pobrać odwołania do domyślnej domeny aplikacji.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>Aby zademonstrować powiadomień o wyjątkach pierwszej szansy w domenie aplikacji

1.  Utwórz `Worker` obiektu w domenie aplikacji, który został utworzony w poprzedniej procedurze. `Worker` Klasy muszą być publiczne i musi pochodzić od klasy <xref:System.MarshalByRefObject>, jak pokazano w kompletnym przykładzie na końcu tego artykułu.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2.  Wywołaj metodę klasy `Worker` obiekt, który zgłasza wyjątek. W tym przykładzie `Thrower` metoda jest wywoływana dwa razy. Podczas pierwszego argumentu metody jest `true`, co powoduje, że metoda przechwycić wyjątek swój własny. Po raz drugi, argument jest `false`i `Main()` metoda przechwytuje wyjątek w domyślnej domeny aplikacji.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3.  Umieść kod w `Thrower` metodę, aby kontrolować, czy metoda obsługuje swój własny wyjątek.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a>Przykład
 Poniższy przykład tworzy domenę aplikacji o nazwie `AD1` i dodaje procedurę obsługi zdarzeń do domeny aplikacji <xref:System.AppDomain.FirstChanceException> zdarzeń. Przykład tworzy wystąpienie `Worker` klasy w domenie aplikacji i wywołuje metodę o nazwie `Thrower` która zgłasza <xref:System.ArgumentException>. W zależności od wartości argumentu metoda przechwytuje wyjątek lub nie można go obsłużyć.

 Każdorazowo `Thrower` metoda zgłasza wyjątek `AD1`, <xref:System.AppDomain.FirstChanceException> zdarzenie jest zgłaszane w `AD1`, i wyświetla komunikat, program obsługi zdarzeń. Środowisko uruchomieniowe wyszukuje następnie obsługi wyjątków. W przypadku pierwszego programu obsługi wyjątków znajduje się w `AD1`. W drugim przypadku nieobsługiwanego wyjątku w `AD1`i zamiast tego zostanie zablokowany w domyślnej domeny aplikacji.

> [!NOTE]
>  Nazwa domyślnej domeny aplikacji jest taka sama jak nazwa pliku wykonywalnego.

 Jeśli dodasz funkcję obsługi <xref:System.AppDomain.FirstChanceException> zdarzenia do domyślnej domeny aplikacji, zdarzenie jest zgłaszane i obsługiwane przed domyślnej domeny aplikacji obsługuje wyjątek. Aby to zobaczyć, Dodaj kod C# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (w języku Visual Basic `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) na początku `Main()`.

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

-   W tym przykładzie jest aplikacją wiersza polecenia. Aby skompilować i uruchomić ten kod w programie Visual Studio, należy dodać kod C# `Console.ReadLine();` (w języku Visual Basic `Console.ReadLine()`) na końcu `Main()`, aby uniemożliwić zamknięcie, zanim może odczytywać dane wyjściowe z okna poleceń.

## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain.FirstChanceException>
