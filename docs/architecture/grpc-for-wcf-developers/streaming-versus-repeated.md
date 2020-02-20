---
title: Usługi przesyłania strumieniowego a powtarzalne pola — gRPC dla deweloperów WCF
description: Porównaj powtarzane pola z usługami przesyłania strumieniowego jako metody przekazywania kolekcji danych przy użyciu gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 0e717df57ba2bb52d63a063072d8a45bf0f7e395
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503373"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>gRPC Streaming Services a powtórzone pola

usługi gRPC zapewniają dwa sposoby zwracania zestawów danych lub listy obiektów. Specyfikacja komunikatów buforów protokołu używa słowa kluczowego `repeated` do deklarowania list lub tablic komunikatów w innym komunikacie. Specyfikacja usługi gRPC używa słowa kluczowego `stream`, aby zadeklarować długotrwałe połączenie trwałe. Za pośrednictwem tego połączenia są wysyłane wiele komunikatów i mogą być przetwarzane pojedynczo. 

Można również użyć funkcji `stream` w przypadku długotrwałych danych czasowych, takich jak powiadomienia lub komunikaty dziennika. Jednak ten rozdział rozważy jego użycie do zwrócenia jednego zestawu danych.

Którego należy użyć, zależy od następujących czynników:

- Całkowity rozmiar zestawu danych.
- Czas, jaki zajęło utworzenie zestawu danych na końcu klienta lub serwera.
- Czy konsument zestawu danych może rozpocząć od razu, jak tylko pierwszy element jest dostępny, lub wymaga kompletny zestaw danych, aby zrobić coś użyteczne.

## <a name="when-to-use-repeated-fields"></a>Kiedy używać `repeated` pól

Dla dowolnego zestawu danych, który jest ograniczony do rozmiaru i który może zostać wygenerowany w całości w krótkim czasie — powiedzmy, poniżej jednej sekundy — należy użyć pola `repeated` w zwykłym komunikacie protobuf. Na przykład w systemie handlu elektronicznego, aby utworzyć listę elementów w ramach zamówienia, prawdopodobnie szybko i lista nie będzie bardzo duża. Zwracanie pojedynczej wiadomości z polem `repeated` jest kolejnością większą niż użycie `stream` i powoduje mniejsze obciążenie sieci.

Jeśli klient potrzebuje wszystkich danych przed rozpoczęciem przetwarzania, a zestaw danych jest wystarczająco mały, aby utworzyć w pamięci, należy rozważyć użycie pola `repeated`. Należy wziąć pod uwagę, nawet jeśli Tworzenie zestawu danych w pamięci na serwerze jest wolniejsze.

## <a name="when-to-use-stream-methods"></a>Kiedy należy używać metod `stream`

Gdy obiekty komunikatów w zestawach danych są potencjalnie bardzo duże, najlepszym rozwiązaniem jest przeniesienie ich przy użyciu żądań lub odpowiedzi przesyłania strumieniowego. Bardziej wydajne jest konstruowanie dużego obiektu w pamięci, zapisanie go w sieci, a następnie zwolnienie zasobów. Takie podejście poprawi skalowalność usługi.

Podobnie należy wysyłać zestawy danych o nieograniczonej wielkości nad strumieniami, aby uniknąć wyczerpania pamięci podczas konstruowania ich.

W przypadku zestawów danych, w których konsument może osobno przetwarzać każdy element, należy rozważyć użycie strumienia, jeśli oznacza to, że ten postęp może zostać wskazany użytkownikowi. Użycie strumienia może zwiększyć czas odpowiedzi aplikacji, ale należy zrównoważyć ją względem ogólnej wydajności aplikacji.

Innym scenariuszem, w którym strumienie mogą być przydatne, jest to, że komunikat jest przetwarzany przez wiele usług. Jeśli każda usługa w łańcuchu zwraca strumień, usługa terminala (czyli Ostatnia z nich w łańcuchu) może rozpocząć Zwracanie komunikatów. Te komunikaty mogą być przetwarzane i przesyłane z powrotem do pierwotnego obiektu żądającego. Obiekt żądający może zwrócić strumień lub agregować wyniki w pojedynczym komunikacie odpowiedzi. Takie podejście pozwala sobie dobrze na wzorce, takie jak MapReduce.

>[!div class="step-by-step"]
>[Poprzednie](migrate-duplex-services.md)
>[dalej](client-libraries.md)
