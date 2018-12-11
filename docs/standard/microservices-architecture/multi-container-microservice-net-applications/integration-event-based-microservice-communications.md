---
title: Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, zdarzenia integracji do zaimplementowania komunikacji oparte na zdarzeniach między mikrousługami.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 844d4bd8ac18bc31b5abeff5882df1f9a4acaab5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147265"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)

Jak opisano wcześniej, korzystając z komunikacji oparte na zdarzeniach, mikrousługi publikuje zdarzenie, gdy występuje coś, co jest istotne, np. gdy aktualizuje jednostkach biznesowych. Inne mikrousług subskrybować tych zdarzeń. Kiedy mikrousługi odbiera zdarzenia, można było uaktualnić swój własny jednostek biznesowych, które mogą prowadzić do więcej zdarzeń opublikowanej. Jest to kwintesencja pojęcia spójności ostatecznej. Ten system publikowania/subskrybowania zwykle odbywa się przy użyciu implementacji magistrali zdarzeń. Magistrali zdarzeń mogą służyć jako interfejs za pomocą interfejsu API potrzebne do subskrybowanie i anulowanie subskrypcji zdarzeń i publikowania zdarzeń. Może też mieć co najmniej jeden implementacje oparty na wszelkie komunikacji między procesami lub obsługi komunikatów, takich jak kolejki komunikatów lub usługi Service bus, który obsługuje komunikacji asynchronicznej i modelu publikowania/subskrybowania.

Zdarzenia można użyć do zaimplementowania transakcji biznesowych, które obejmują wiele usług, co daje spójności ostatecznej między tymi usługami. Transakcja ostatecznie spójną składa się z szeregu rozproszonych działań. W każdej akcji mikrousług aktualizacji jednostki biznesowe i publikuje zdarzenie, które wyzwala akcję dalej.

![Mikrousługi wykazu, za pomocą oparte na zdarzeniach komunikację za pośrednictwem magistrali zdarzeń, aby osiągnąć spójność z koszyka i dodatkowe mikrousług.](./media/image19.png)

**Rysunek 6-18**. Komunikacja oparte na zdarzeniach, oparte na magistrali zdarzeń

W tej sekcji opisano, jak można zaimplementować ten typ komunikacji przy użyciu platformy .NET przy użyciu interfejsu magistrali zdarzeń generycznych, jak pokazano w rysunek 6-18. Istnieje wiele potencjalnych implementacji przy użyciu różnych technologii lub infrastruktury, takich jak RabbitMQ, usługi Azure Service Bus lub wszelkich innych firm typu open source lub komercyjnymi usługi Service bus.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Za pomocą magistrali komunikatów brokerów i usług dla systemów produkcyjnych.

Jak wspomniano w sekcji architektury, możesz wybrać wiele technologii obsługi komunikatów do implementowania usługi Service bus zdarzenie abstrakcyjne. Jednak te technologie są na różnych poziomach. Na przykład oprogramowania RabbitMQ, transportu brokera obsługi komunikatów, jest na poziomie niższym niż produktów komercyjnych, takich jak usługi Azure Service Bus, NServiceBus, MassTransit lub Brighter. Większość tych produktów mogą działać na podstawie RabbitMQ lub Azure Service Bus. Wybór produktu zależy od tego, jak wiele funkcji i ile out-of--box skalowalność potrzebne dla aplikacji.

Implementowanie tylko zdarzenia magistrali z koncepcji dla swojego środowiska programowania, jak w poniższym przykładzie w ramach aplikacji eShopOnContainers proste wdrażanie na podstawie RabbitMQ uruchomionego jako kontener może być wystarczająca. Ale w przypadku o kluczowym znaczeniu oraz systemów produkcyjnych, które wymagają wysokiej skalowalności, warto do oceny i przy użyciu usługi Azure Service Bus.

Jeśli potrzebujesz abstrakcji wysokiego poziomu i bardziej zaawansowane funkcje, takie jak [Sagach](https://docs.particular.net/nservicebus/sagas/) dla procesów długotrwałych, które dzięki niej programowanie rozproszonych łatwiejsze innych komercyjnych i open-source usługa autobusów, takich jak NServiceBus, MassTransit, i Brighter są warte dokonanie oceny oprogramowania. W tym przypadku abstrakcje i interfejsu API do używania zazwyczaj będzie bezpośrednio te udostępniane przez te autobusów wysokiego poziomu usługi zamiast własnego abstrakcje (takich jak [abstrakcje magistrali zdarzenie proste podane w ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). Dla tej sprawy, można zbadać [forked przy użyciu NServiceBus w ramach aplikacji eShopOnContainers](https://go.particular.net/eShopOnContainers) (dodatkowe przykład pochodnej implementowany przez konkretnego oprogramowania)

Oczywiście zawsze można zbudować własne funkcje magistrali usługi na podstawie technologii niższego poziomu, takie jak RabbitMQ i platformy Docker, ale czynności niezbędne do "wynalazł koła" może być zbyt kosztowne dla aplikacji przedsiębiorstwa niestandardowych.

Aby przywołują: Przykładowe zdarzenia magistrali abstrakcje i implementacji przedstawionym w ramach aplikacji eShopOnContainers próbki są przeznaczone do służyć jedynie jako Weryfikacja koncepcji. Gdy okaże się, chcesz mieć komunikacji asynchronicznej i oparte na zdarzeniach, jak wyjaśniono w bieżącej sekcji, należy wybrać produkt magistrali usług, który najlepiej spełnia Twoje potrzeby w środowisku produkcyjnym.

## <a name="integration-events"></a>Zdarzenia integracji

Integracja zdarzenia są używane do pobierania stanu domeny w synchronizacji w wielu mikrousługach lub systemy zewnętrzne. Polega to na publikowanie zdarzenia integracji spoza mikrousług. Po opublikowaniu zdarzenia do wielu mikrousług odbiorcy (na tyle mikrousług, zgodnie z subskrybowanym zdarzenia integracji) obsługi odpowiedniego zdarzenia w poszczególne mikrousługi odbiorcy obsługuje zdarzenie.

Zdarzenie integracji jest zasadniczo klasą przechowywania danych, jak w poniższym przykładzie:

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

Zdarzenia integracji można zdefiniować na poziomie aplikacji, poszczególne mikrousługi, więc one są całkowicie niezależni od innych mikrousług, w sposób porównywalny z jak modele widoków są zdefiniowane w serwera i klienta. Co nie jest zalecane jest udostępnianie wspólnej biblioteki zdarzenia integracji między wiele mikrousług; tych czynności będzie można sprzężenia tych mikrousług przy użyciu biblioteki pojedyncze zdarzenie definicji danych. Czy chcesz to zrobić dla takie same powodów, dla których nie chcesz udostępniać Wspólny model domeny w wielu mikrousługach: mikrousług musi być całkowicie autonomicznych.

Istnieje tylko kilka rodzajów bibliotek, które powinny współużytkować między mikrousług. Jeden jest bibliotek, które są bloki gotowych aplikacji, takie jak [interfejsu API klienta magistrali zdarzeń](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), jak w ramach aplikacji eShopOnContainers. Innym jest bibliotek, które tworzą narzędzia, które również zostaną udostępnione jako części NuGet, takich jak serializatory JSON.

## <a name="the-event-bus"></a>Magistrali zdarzeń

Magistrali zdarzeń umożliwia publikowania/subskrybowania — styl komunikację między mikrousługami bez składniki, które jawnie wiedzieć, jak pokazano w rysunek 6-19.

![Wzorzec publikowania/subskrybowania podstawowe Mikrousług A publikuje w magistrali zdarzeń, który rozprowadza do mikrousług susbcribing B i C, bez znajomości susbcribers wydawcy.](./media/image20.png)

**Rysunek 6-19**. Podstawowe informacje o magistrali zdarzeń publikowania/subskrybowania

Magistrali zdarzeń dotyczące wzorzec obserwatora i Publikuj — Subskrybuj wzorca.

### <a name="observer-pattern"></a>Wzorzec obserwatora

W [wzorzec obserwatora](https://en.wikipedia.org/wiki/Observer_pattern), obiekt podstawowy (znanych jako możliwość obserwowania) powiadamia innych zainteresowanych obiektów (znanych jako obserwatorzy) z istotnymi informacjami (zdarzenia).

### <a name="publishsubscribe-pubsub-pattern"></a>Wzorzec publikowania/subskrybowania (Pub/Sub) 

Celem [wzorca publikowania/subskrypcji](https://msdn.microsoft.com/library/ff649664.aspx) jest taka sama jak wzorzec obserwatora: chcesz powiadomić inne usługi, w przypadku wystąpienia określonych zdarzeń została wykonana. Ale ma jedną istotną różnicą między wzorców obserwatora i Pub/Sub. We wzorcu obserwatora emisji odbywa się bezpośrednio z obserwowalnymi na obserwatorów, dzięki czemu "znane" siebie nawzajem. Ale gdy przy użyciu wzorca publikowania/subskrybowania, jest trzecim składnikiem o nazwie brokera lub broker lub zdarzeń magistrali komunikatów, który jest znany wydawcy i subskrybenta. W związku z tym gdy przy użyciu wzorca publikowania/subskrybowania wydawcy i subskrybenci są dokładnie odłączone dzięki brokera magistrali lub wiadomości wymienionych zdarzeń.

### <a name="the-middleman-or-event-bus"></a>Service bus pośredników lub zdarzenie 

Jak osiągnąć anonimowości między wydawcą a transakcyjnym subskrybentem? Łatwo jest umożliwiają pośredników zajmie się całą komunikację. Magistrali zdarzeń jest jeden taki pośredników.

Magistrali zdarzeń zwykle składa się z dwóch części:

-   Abstrakcja lub interfejs.

-   Co najmniej jeden implementacji.

W rysunek 6-19 możesz zobaczyć jak to zrobić, z punktu widzenia aplikacji, magistrali zdarzeń to nic innego niż kanału Pub/Sub. Sposób zaimplementowania tej komunikacji asynchronicznej może się różnić. Tak, aby można przełączać się między nimi, w zależności od wymagań środowiska (na przykład, środowisko produkcyjne i środowiska deweloperskie) może mieć wiele implementacji.

W rysunek 6 – 20 znajduje abstrakcję magistrali zdarzeń z wielu implementacjach oparte na infrastruktury obsługi komunikatów technologii, takich jak RabbitMQ, usługi Azure Service Bus lub innym brokerem/komunikatu o zdarzeniu.

![Warto mieć magistrali zdarzeń zdefiniowanych za pomocą interfejsu, więc można ją wdrożyć za pomocą kilku tecnologies, takich jak usługi RabbitMQ usługi Azure Service bus lub inne osoby.](./media/image21.png)

**Rysunek 6 - 20.** Wiele implementacji magistrali zdarzeń

Jednakże i jak wspomniano wcześniej przy użyciu własnych abstrakcje (interfejsu magistrali zdarzeń) jest dobra, tylko wtedy, gdy potrzebujesz funkcji magistrali zdarzeń w wersji basic, są obsługiwane przez Twoje abstrakcje. Jeśli potrzebujesz bardziej rozbudowane funkcje magistrali usług, należy prawdopodobnie używać interfejsu API i abstrakcje dostarczone przez Twojego preferowanego komercyjnych usługi Service bus zamiast własne elementy abstrakcji.

### <a name="defining-an-event-bus-interface"></a>Definiowanie interfejsu magistrali zdarzeń

Zacznijmy od kodu implementacji interfejsu magistrali zdarzeń i możliwe implementacje dla celów eksploracji. Interfejs powinna być ogólny i prostego, tak jak w poniższym interfejsu.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);

    void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>;

    void SubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void UnsubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void Unsubscribe<T, TH>()
        where TH : IIntegrationEventHandler<T>
        where T : IntegrationEvent;
}
```

`Publish` Metoda jest prosta. Magistrali zdarzeń będzie emitować zdarzenia integracji przekazywane do niego wszystkie mikrousługi lub nawet aplikacji zewnętrznej, zasubskrybować tego zdarzenia. Ta metoda jest używana przez mikrousług, która jest publikowanie zdarzenia.

`Subscribe` Metody (może mieć kilka implementacji w zależności od argumentów) są używane przez mikrousług, które chcesz odbierać zdarzenia. Ta metoda ma dwa argumenty. Pierwsza to zdarzenie integracji, aby subskrybować (`IntegrationEvent`). Drugi argument funkcji jest integracja zdarzenie obsługi (lub metody wywołania zwrotnego), o nazwie `IIntegrationEventHandler<T>`, które zostaną wykonane podczas mikrousług odbiornik pobiera ten komunikat zdarzenia integracji.

>[!div class="step-by-step"]
>[Poprzednie](database-server-container.md)
>[dalej](rabbitmq-event-bus-development-test-environment.md)