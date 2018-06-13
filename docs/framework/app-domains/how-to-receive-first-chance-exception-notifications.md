---
title: 'Porady: odbieranie powiadomień o wyjątkach pierwszej szansy'
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
ms.openlocfilehash: d48aa2029d11c884b81aa5181845e71b2756d629
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744372"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Porady: odbieranie powiadomień o wyjątkach pierwszej szansy
<xref:System.AppDomain.FirstChanceException> Zdarzenie <xref:System.AppDomain> klasa pozwala na powiadomienie wyjątek, przed wspólnego języka środowiska uruchomieniowego zostało uruchomione, wyszukiwanie programy obsługi wyjątków.  
  
 Zdarzenie jest wywoływane na poziomie domeny aplikacji. Wykonanie wątku mogą przejść przez wiele domen aplikacji, więc wyjątek, który jest nieobsługiwany w jednej domenie aplikacji może być obsługiwane w innej domenie aplikacji. Powiadomienia występuje w każdej domenie aplikacji, która została dodana obsługa zdarzeń, dopóki domeny aplikacji obsługuje wyjątek.  
  
 Procedury i przykłady w tym artykule pokazano, jak otrzymywać powiadomienia o wyjątkach pierwszej szansy w prosty program, który ma jedną domenę aplikacji, w który tworzenia domeny aplikacji.  
  
 Na przykład bardziej złożonych, obejmującej wiele domen aplikacji, zobacz przykład <xref:System.AppDomain.FirstChanceException> zdarzeń.  
  
## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Odbieranie powiadomień o wyjątkach pierwszej szansy w domyślnej domeny aplikacji  
 W poniższej procedurze punkt wejścia dla aplikacji, `Main()` metoda, jest uruchamiana w domyślnej domeny aplikacji.  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>Aby zademonstrować powiadomienia o wyjątkach pierwszej szansy w domyślnej domeny aplikacji  
  
1.  Definiowanie procedury obsługi zdarzeń dla <xref:System.AppDomain.FirstChanceException> zdarzeń za pomocą wyrażenia lambda funkcji i dołączenie go do zdarzenia. W tym przykładzie programu obsługi zdarzeń wyświetla nazwę domeny aplikacji, w którym zdarzenie zostało obsłużone i wyjątków <xref:System.Exception.Message%2A> właściwości.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]  
  
2.  Zgłoś wyjątek i jego catch. Zanim program obsługi wyjątku lokalizuje środowiska uruchomieniowego <xref:System.AppDomain.FirstChanceException> zdarzenie jest wywoływane i zostanie wyświetlony komunikat. Ten komunikat występuje komunikat, który jest wyświetlany przez program obsługi wyjątku.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]  
  
3.  Zgłoś wyjątek, ale nie catch. Przed środowiska uruchomieniowego szuka obsługi wyjątków, <xref:System.AppDomain.FirstChanceException> zdarzenie jest wywoływane i zostanie wyświetlony komunikat. Nie bez obsługi wyjątków, dlatego kończy aplikacji.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]  
  
     Kod, który jest wyświetlany w trzech pierwszych kroków tej procedury formularzy aplikacji konsoli ukończone. Dane wyjściowe z aplikacji różni się w zależności od nazwy pliku .exe, ponieważ nazwa domyślnej domeny aplikacji obejmuje nazwę i rozszerzenie pliku .exe. Zobacz następujące przykładowe dane wyjściowe.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]  
  
## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Odbieranie powiadomień o wyjątkach pierwszej szansy w innej domenie aplikacji  
 Jeśli program zawiera więcej niż jedną domenę aplikacji, można wybrać domen aplikacji otrzymywać powiadomienia.  
  
#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Aby otrzymywać powiadomienia o wyjątkach pierwszej szansy w tworzonej domeny aplikacji  
  
1.  Definiowanie procedury obsługi zdarzeń dla <xref:System.AppDomain.FirstChanceException> zdarzeń. W tym przykładzie użyto `static` — metoda (`Shared` metody w języku Visual Basic) która wyświetla nazwę domeny aplikacji, w którym zdarzenie zostało obsłużone i wyjątków <xref:System.Exception.Message%2A> właściwości.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]  
  
2.  Tworzenie domeny aplikacji i Dodaj program obsługi zdarzeń do <xref:System.AppDomain.FirstChanceException> zdarzeń dla tej domeny aplikacji. W tym przykładzie domena aplikacji o nazwie `AD1`.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]  
  
     To zdarzenie w domenie aplikacji domyślne może obsługiwać w taki sam sposób. Użyj `static` (`Shared` w języku Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> właściwości w `Main()` można pobrać odwołania do domyślnej domeny aplikacji.  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>Aby zademonstrować powiadomienia o wyjątkach pierwszej szansy w domenie aplikacji  
  
1.  Utwórz `Worker` obiektu w domenie aplikacji, który został utworzony w poprzedniej procedurze. `Worker` Klasy muszą być publiczne i musi pochodzić od <xref:System.MarshalByRefObject>, jak pokazano w przykładzie pełną na końcu tego artykułu.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]  
  
2.  Wywołaj metodę `Worker` obiekt, który zgłasza wyjątek. W tym przykładzie `Thrower` metoda jest wywoływana dwukrotnie. Podczas pierwszego argumentu metody jest `true`, co powoduje, że metoda własną wyjątek. Raz drugi argument jest `false`i `Main()` metody przechwytuje wyjątek w domyślnej domeny aplikacji.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]  
  
3.  Umieść kod w `Thrower` metody kontrolowania, czy metoda obsługuje własny wyjątek.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy domenę aplikacji o nazwie `AD1` i dodanie obsługi zdarzeń do domeny aplikacji <xref:System.AppDomain.FirstChanceException> zdarzeń. W przykładzie jest tworzony wystąpienia `Worker` klasy w domenie aplikacji i wywołuje metodę o nazwie `Thrower` który zgłasza <xref:System.ArgumentException>. W zależności od wartości argumentu metody przechwytuje wyjątek lub nie powiedzie się do jego obsługi.  
  
 Zawsze `Thrower` metoda zgłasza wyjątek `AD1`, <xref:System.AppDomain.FirstChanceException> zdarzenie jest zgłaszane w `AD1`, i program obsługi zdarzeń zostanie wyświetlony komunikat. Środowisko uruchomieniowe następnie szuka obsługi wyjątków. W pierwszym przypadku program obsługi wyjątku zostanie znaleziony w `AD1`. W drugim przypadku nieobsługiwany wyjątek w `AD1`, a zamiast tego zostanie przechwycony w domyślnej domeny aplikacji.  
  
> [!NOTE]
>  Nazwa domyślnej domeny aplikacji jest taka sama jak nazwa pliku wykonywalnego.  
  
 Po dodaniu obsługi dla <xref:System.AppDomain.FirstChanceException> zdarzenia do domyślnej domeny aplikacji, zdarzenie jest wywoływane i obsługiwane przed domyślnej domeny aplikacji obsługuje wyjątek. Aby to sprawdzić, należy dodać kodu C# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (w języku Visual Basic `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) na początku `Main()`.  
  
 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   W tym przykładzie jest aplikacją wiersza polecenia. Aby skompilować i uruchomić ten kod [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], Dodaj kod C# `Console.ReadLine();` (w języku Visual Basic `Console.ReadLine()`) na końcu `Main()`, aby uniemożliwić zamknięcie przed przeczytaniem dane wyjściowe okna poleceń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppDomain.FirstChanceException>
