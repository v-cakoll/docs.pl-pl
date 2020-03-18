---
title: Usługi przesyłania strumieniowego a powtarzające się pola - gRPC dla deweloperów WCF
description: Porównaj powtarzające się pola z usługami przesyłania strumieniowego jako sposoby przekazywania kolekcji danych przy użyciu gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 542ebc393f9c9c1ad717d02d01fab33d85c18917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147753"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>Usługi przesyłania strumieniowego gRPC a powtarzające się pola

Usługi gRPC zapewniają dwa sposoby zwracania zestawów danych lub listy obiektów. Specyfikacja komunikatu Bufory `repeated` protokołu używa słowa kluczowego do deklarowania list lub tablic wiadomości w ramach innej wiadomości. Specyfikacja usługi gRPC `stream` używa słowa kluczowego do deklarowania długotrwałego połączenia trwałego. Za pomocą tego połączenia wiele wiadomości są wysyłane i mogą być przetwarzane, indywidualnie.

Można również użyć `stream` tej funkcji dla długotrwałych danych czasowych, takich jak powiadomienia lub komunikaty dziennika. Ale ten rozdział rozważy jego użycie do zwracania pojedynczego zestawu danych.

Którego należy użyć, zależy od takich czynników, jak:

- Ogólny rozmiar zestawu danych.
- Czas, który trzeba było utworzyć zestaw danych na końcu klienta lub serwera.
- Czy konsument zestawu danych może rozpocząć działanie na nim tak szybko, jak pierwszy element jest dostępny lub potrzebuje pełnego zestawu danych, aby zrobić coś pożytecznego.

## <a name="when-to-use-repeated-fields"></a>Kiedy używać `repeated` pól

W przypadku każdego zestawu danych, który jest ograniczony rozmiarem i który może być generowany w całości w krótkim `repeated` czasie — powiedzmy, poniżej jednej sekundy — należy użyć pola w zwykłej wiadomości Protobuf. Na przykład w systemie e-commerce, aby zbudować listę elementów w zamówieniu jest prawdopodobnie szybkie, a lista nie będzie bardzo duża. Zwracanie pojedynczej wiadomości `repeated` z polem jest o `stream` rząd wielkości szybciej niż przy użyciu i wiąże się z mniejszym obciążeniem sieciowym.

Jeśli klient potrzebuje wszystkich danych przed rozpoczęciem przetwarzania go, a zestaw danych jest `repeated` wystarczająco mały, aby skonstruować w pamięci, należy rozważyć użycie pola. Należy wziąć pod uwagę, nawet jeśli tworzenie zestawu danych w pamięci na serwerze jest wolniejsze.

## <a name="when-to-use-stream-methods"></a>Kiedy stosować `stream` metody

Gdy obiekty wiadomości w zestawach danych są potencjalnie bardzo duże, najlepiej jest przenieść je przy użyciu żądań przesyłania strumieniowego lub odpowiedzi. Bardziej efektywne jest konstruowanie dużego obiektu w pamięci, zapisywanie go w sieci, a następnie zwalnianie zasobów. Takie podejście poprawi skalowalność usługi.

Podobnie należy wysyłać zestawy danych o nieograniczonym rozmiarze przez strumienie, aby uniknąć wyczerpania pamięci podczas konstruowania ich.

W przypadku zestawów danych, w których konsument może oddzielnie przetwarzać każdy element, należy rozważyć użycie strumienia, jeśli oznacza to, że postęp może być wskazany użytkownikowi. Za pomocą strumienia można poprawić czas reakcji aplikacji, ale należy zrównoważyć go z ogólną wydajność aplikacji.

Innym scenariuszem, w którym strumienie mogą być przydatne jest, gdy komunikat jest przetwarzany w wielu usługach. Jeśli każda usługa w łańcuchu zwraca strumień, usługa terminalowa (czyli ostatnia w łańcuchu) może rozpocząć zwracanie wiadomości. Te wiadomości mogą być przetwarzane i przekazywane z powrotem wzdłuż łańcucha do oryginalnego żądaczy. Żądającego można zwrócić strumień lub agregować wyniki w jednej wiadomości odpowiedzi. Takie podejście nadaje się również do wzorców, takich jak MapReduce.

>[!div class="step-by-step"]
>[Poprzedni](migrate-duplex-services.md)
>[następny](client-libraries.md)
