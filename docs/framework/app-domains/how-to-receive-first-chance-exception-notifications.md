---
title: 'Instrukcje: Odbieranie powiadomień o wyjątkach pierwszej szansy'
description: Otrzymuj powiadomienia o wyjątkach pierwszej szansy w programie .NET przy użyciu zdarzenia FirstChanceException klasy AppDomain przed wyszukiwaniem obsługi wyjątków przez środowisko CLR.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
ms.openlocfilehash: e8b5ae5fb69c7befd329316aee11523f79d73fcd
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104745"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Instrukcje: Odbieranie powiadomień o wyjątkach pierwszej szansy
<xref:System.AppDomain.FirstChanceException>Zdarzenie <xref:System.AppDomain> klasy pozwala otrzymać powiadomienie, że zgłoszono wyjątek, zanim środowisko uruchomieniowe języka wspólnego zacznie wyszukiwać obsługę wyjątków.

 Zdarzenie jest zgłaszane na poziomie domeny aplikacji. Wątek wykonywania może przechodzić przez wiele domen aplikacji, więc wyjątek, który jest nieobsługiwany w jednej domenie aplikacji, może być obsługiwany w innej domenie aplikacji. Powiadomienie odbywa się w każdej domenie aplikacji, która dodała procedurę obsługi dla zdarzenia, dopóki domena aplikacji obsłuży wyjątek.

 Procedury i przykłady w tym artykule pokazują, jak odbierać powiadomienia o wyjątkach pierwszej szansy w prostym programie, który ma jedną domenę aplikacji, i w utworzonej domenie aplikacji.

 Aby uzyskać bardziej złożony przykład obejmujący kilka domen aplikacji, zobacz przykład <xref:System.AppDomain.FirstChanceException> zdarzenia.

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Otrzymywanie powiadomień o wyjątkach pierwszej szansy w domenie domyślnej aplikacji
 W poniższej procedurze punkt wejścia dla aplikacji, `Main()` Metoda uruchamiana w domyślnej domenie aplikacji.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>Aby przedstawić powiadomienia o wyjątkach pierwszej szansy w domenie domyślnej aplikacji

1. Zdefiniuj procedurę obsługi zdarzeń dla <xref:System.AppDomain.FirstChanceException> zdarzenia przy użyciu funkcji lambda i Dołącz ją do zdarzenia. W tym przykładzie program obsługi zdarzeń drukuje nazwę domeny aplikacji, w której zostało obsłużone zdarzenie, oraz <xref:System.Exception.Message%2A> Właściwość wyjątku.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2. Zgłoś wyjątek i Przechwyć go. Zanim środowisko uruchomieniowe odnajdzie procedurę obsługi wyjątków, <xref:System.AppDomain.FirstChanceException> zdarzenie jest zgłaszane i wyświetla komunikat. Po tym komunikacie następuje komunikat, który jest wyświetlany przez program obsługi wyjątków.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3. Zgłoś wyjątek, ale nie należy go przechwycić. Zanim środowisko uruchomieniowe wyszuka procedurę obsługi wyjątków, <xref:System.AppDomain.FirstChanceException> zdarzenie jest zgłaszane i wyświetla komunikat. Brak obsługi wyjątków, więc aplikacja kończy działanie.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     Kod, który jest wyświetlany w pierwszych trzech krokach tej procedury, stanowi kompletną aplikację konsolową. Dane wyjściowe aplikacji różnią się w zależności od nazwy pliku. exe, ponieważ nazwa domyślnej domeny aplikacji składa się z nazwy i rozszerzenia pliku. exe. Poniżej znajdują się przykładowe dane wyjściowe.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Otrzymywanie powiadomień o wyjątkach pierwszej szansy w innej domenie aplikacji
 Jeśli program zawiera więcej niż jedną domenę aplikacji, możesz wybrać, które domeny aplikacji mają otrzymywać powiadomienia.

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Aby otrzymywać powiadomienia o wyjątkach pierwszej szansy w domenie aplikacji, którą tworzysz

1. Zdefiniuj procedurę obsługi zdarzeń dla <xref:System.AppDomain.FirstChanceException> zdarzenia. W tym przykładzie użyto `static` metody ( `Shared` metoda w Visual Basic), która drukuje nazwę domeny aplikacji, w której zostało obsłużone zdarzenie, oraz <xref:System.Exception.Message%2A> Właściwość wyjątku.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2. Utwórz domenę aplikacji i Dodaj procedurę obsługi zdarzeń do <xref:System.AppDomain.FirstChanceException> zdarzenia dla tej domeny aplikacji. W tym przykładzie domena aplikacji ma nazwę `AD1` .

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     To zdarzenie można obsłużyć w domyślnej domenie aplikacji w taki sam sposób. Użyj `static` właściwości ( `Shared` w Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> w programie, `Main()` Aby uzyskać odwołanie do domyślnej domeny aplikacji.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>Aby przedstawić powiadomienia o wyjątkach pierwszej szansy w domenie aplikacji

1. Utwórz `Worker` obiekt w domenie aplikacji, który został utworzony w poprzedniej procedurze. `Worker`Klasa musi być publiczna i musi pochodzić od <xref:System.MarshalByRefObject> , jak pokazano w kompletnym przykładzie na końcu tego artykułu.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2. Wywoływanie metody `Worker` obiektu, który zgłasza wyjątek. W tym przykładzie `Thrower` Metoda jest wywoływana dwukrotnie. Po raz pierwszy argument metody ma wartość `true` , która powoduje, że metoda będzie przechwytywać własny wyjątek. Drugi raz, argument jest `false` , a `Main()` Metoda przechwytuje wyjątek w domyślnej domenie aplikacji.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3. Umieść kod w `Thrower` metodzie, aby określić, czy metoda obsługuje swój własny wyjątek.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a>Przykład
 Poniższy przykład tworzy domenę aplikacji o nazwie `AD1` i dodaje procedurę obsługi zdarzeń do zdarzenia domeny aplikacji <xref:System.AppDomain.FirstChanceException> . Przykład tworzy wystąpienie `Worker` klasy w domenie aplikacji i wywołuje metodę o nazwie `Thrower` , która zgłasza <xref:System.ArgumentException> . W zależności od wartości argumentu Metoda przechwytuje wyjątek lub nie można jej obsłużyć.

 Za każdym razem, gdy `Thrower` Metoda zgłasza wyjątek w `AD1` , <xref:System.AppDomain.FirstChanceException> zdarzenie jest zgłaszane w `AD1` , a program obsługi zdarzeń wyświetla komunikat. Środowisko uruchomieniowe następnie szuka programu obsługi wyjątków. W pierwszym przypadku program obsługi wyjątków znajduje się w `AD1` . W drugim przypadku wyjątek jest nieobsługiwany w `AD1` , a zamiast tego jest przechwytywany w domyślnej domenie aplikacji.

> [!NOTE]
> Nazwa domyślnej domeny aplikacji jest taka sama jak nazwa pliku wykonywalnego.

 Jeśli dodasz procedurę obsługi dla <xref:System.AppDomain.FirstChanceException> zdarzenia do domyślnej domeny aplikacji, zdarzenie jest zgłaszane i obsługiwane, zanim domyślna domena aplikacji obsłuży wyjątek. Aby to sprawdzić, Dodaj kod C# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (w Visual Basic, `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException` ) na początku `Main()` .

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.AppDomain.FirstChanceException>
