---
title: gRPC Streaming Services a powtórzone pola — gRPC dla deweloperów WCF
description: Porównywanie powtarzających się pól z usługami przesyłania strumieniowego jako metody przekazywania kolekcji danych za pomocą gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: f2f13776586607ed489c45ebb324c0c5713bed99
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966923"
---
# <a name="grpc-streaming-services-versus-repeated-fields"></a>gRPC Streaming Services a powtórzone pola

usługi gRPC zapewniają dwa sposoby zwracania zestawów danych lub listy obiektów. Specyfikacja komunikatów buforów protokołu używa słowa kluczowego `repeated` do deklarowania list lub tablic komunikatów w innym komunikacie. Specyfikacja usługi gRPC używa słowa kluczowego `stream`, aby zadeklarować długotrwałe, trwałe połączenie, za pomocą którego są wysyłane wiele komunikatów i może być przetwarzane pojedynczo. Funkcja `stream` może być również używana do długotrwałych danych czasowych, takich jak powiadomienia lub komunikaty dziennika, ale ten rozdział będzie rozważał użycie do zwrócenia jednego zestawu danych.

Którego należy użyć, zależy od różnych czynników, takich jak całkowity rozmiar zestawu danych, czas potrzebny do utworzenia zestawu danych na końcu klienta lub serwera oraz czy konsument zestawu danych może zacząć od razu po udostępnieniu pierwszego elementu lub potrzebuje kompletnego zestawu danych, aby wykonać wszelkie użyteczne.

## <a name="when-to-use-repeated-fields"></a>Kiedy używać `repeated` pól

Dla dowolnego zestawu danych, który jest ograniczony do rozmiaru i który może zostać wygenerowany w całości w krótkim czasie — powiedzmy, poniżej jednej sekundy — należy użyć pola `repeated` w zwykłym komunikacie protobuf. Na przykład w systemie handlu elektronicznego, aby utworzyć listę elementów w ramach zamówienia, prawdopodobnie szybko i lista nie będzie bardzo duża. Zwracanie pojedynczej wiadomości z polem `repeated` jest kolejnością większą niż użycie `stream` i powoduje mniejsze obciążenie sieci.

Jeśli klient potrzebuje wszystkich danych przed rozpoczęciem przetwarzania, a zestaw danych jest wystarczająco mały, aby utworzyć w pamięci, należy rozważyć użycie pola `repeated`, nawet jeśli rzeczywiste Tworzenie zestawu danych w pamięci na serwerze jest wolniejsze.

## <a name="when-to-use-stream-methods"></a>Kiedy należy używać metod `stream`

Zestawy danych, w których obiekty komunikatów są potencjalnie bardzo duże, są najlepiej przesłane przy użyciu żądań przesyłania strumieniowego lub odpowiedzi. Bardziej wydajne jest konstruowanie dużego obiektu w pamięci, zapisanie go w sieci, a następnie zwolnienie zasobów. Takie podejście poprawi skalowalność usługi.

Podobnie zestawy danych o nieograniczonej wielkości powinny być wysyłane za pośrednictwem strumieni, aby uniknąć wyczerpania pamięci podczas konstruowania ich.

W przypadku zestawów danych, w których poszczególne elementy mogą być przetwarzane oddzielnie przez konsumenta, należy rozważyć użycie strumienia, jeśli oznacza to, że ten postęp może być wskazany użytkownikowi końcowemu. Może to poprawić pozorny czas odpowiedzi aplikacji, chociaż powinna być zrównoważona względem ogólnej wydajności aplikacji.

Innym scenariuszem, w którym strumienie mogą być przydatne, jest to, że komunikat jest przetwarzany przez wiele usług. Jeśli każda usługa w łańcuchu zwraca strumień, usługa terminala (czyli Ostatnia z nich w łańcuchu) może rozpocząć Zwracanie komunikatów, które mogą być przetwarzane i przekazywać z powrotem do pierwotnego obiektu żądającego, co może spowodować zwrócenie strumienia lub agregowanie daje w wyniku pojedynczy komunikat odpowiedzi. Takie podejście pozwala sobie dobrze na wzorce, takie jak mapa/zmniejszenie.

>[!div class="step-by-step"]
>[Poprzedni](migrate-duplex-services.md)
>[Następny](client-libraries.md)
