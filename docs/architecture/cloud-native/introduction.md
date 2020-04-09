---
title: Wprowadzenie do natywnych aplikacji w chmurze
description: Dowiedz się więcej o obliczeniach natywnych dla chmury
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: c9ffd34ec3deb04abddbbf85a9e5a6ed2b57c8f9
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989054"
---
# <a name="introduction-to-cloud-native-applications"></a>Wprowadzenie do natywnych aplikacji w chmurze

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kolejny dzień, w biurze, pracuje nad "następną wielką rzeczą".

Twój telefon dzwoni. To twój przyjazny rekruter - ten, który dzwoni do Ciebie dwa razy dziennie o nowych miejscach pracy.

Ale tym razem jest inaczej: Start-up, kapitał własny i mnóstwo funduszy.

Wzmianka o chmurze i najnowocześniejszej technologii popycha cię ponad krawędź.

Przewijanie do przodu o kilka tygodni, a teraz jesteś nowym pracownikiem w sesji projektowej, która projektuje główną aplikację eCommerce. Masz zamiar wraz z innymi wiodącymi witrynami eCommerce.

Jak go zbudujesz?

Jeśli zastosujesz się do wskazówek z ostatnich 15 lat, najprawdopodobniej zbudujesz system pokazany na rysunku 1.1.

![Tradycyjna monolityczna konstrukcja](./media/monolithic-design.png)

**Rysunek 1-1**. Tradycyjna monolityczna konstrukcja

Konstruujesz dużą podstawową aplikację zawierającą całą logikę domeny. Zawiera moduły, takie jak tożsamość, katalog, zamawianie i inne. Podstawowa aplikacja komunikuje się z dużą relacyjną bazą danych. Rdzeń udostępnia funkcje za pośrednictwem interfejsu HTML.

Gratulacje!  Właśnie utworzono aplikację monolityczną.

Nie wszystko jest złe. Monolity oferują pewne wyraźne zalety. Na przykład, są one proste do ...

- kompilacja
- test
- Wdrożyć
- troubleshoot
- scale

Wiele udanych aplikacji, które istnieją dzisiaj zostały utworzone jako monolity. Aplikacja jest hitem i nadal ewoluować, iteracji po iteracji, dodając coraz więcej funkcji.

W pewnym momencie jednak zaczynasz czuć się nieswojo. Znajdziesz się utraty kontroli nad aplikacją. W miarę upływu czasu uczucie staje się bardziej intensywne i w końcu wchodzisz w stan znany jako **Cykl Strachu.**

- Aplikacja stała się tak przytłaczająco skomplikowana, że żadna osoba jej nie rozumie.
- Boisz się wprowadzania zmian - każda zmiana ma niezamierzone i kosztowne skutki uboczne.
- Nowe funkcje / poprawki stają się trudne, czasochłonne i kosztowne do wdrożenia.
- Każda wersja tak małe, jak może być wymaga pełnego wdrożenia całej aplikacji.
- Jeden niestabilny komponent może ulec awarii całego systemu.
- Nowe technologie i struktury nie są możliwe.
- Trudno jest wdrożyć metody agile dostawy.
- Erozja architektury ustawia się w miarę pogarszania się podstawy kodu z niekończącymi się "specjalnymi przypadkami".
- Konsultanci mówią, aby go przepisać.

Wiele organizacji rozwiązało monolityczny cykl strachu, przyjmując natywne podejście do systemów budowania. Rysunek 1-2 przedstawia ten sam system zbudowany stosując natywne dla chmury techniki i praktyki.

![Projektowanie natywne dla chmury](./media/cloud-native-design.png)

**Rysunek 1-2**. Projektowanie natywne dla chmury

Należy zauważyć, jak aplikacja jest rozłożona na zestaw małych mikrousług izolowanych. Każda usługa jest niezależna i hermetyzuje własny kod, dane i zależności. Każdy z nich jest wdrażany w kontenerze oprogramowania i zarządzany przez koordynatora kontenera. Zamiast dużej relacyjnej bazy danych każda usługa jest właścicielem magazynu danych, którego typ różni się w zależności od potrzeb danych. Zwróć uwagę, jak niektóre usługi zależą od relacyjnej bazy danych, ale inne od baz danych NoSQL. Jedna usługa przechowuje swój stan w rozproszonej pamięci podręcznej. Zwróć uwagę, jak wszystkie trasy ruchu za pośrednictwem usługi bramy interfejsu API, która jest odpowiedzialna za routing ruchu do podstawowych usług zaplecza i wymuszanie wielu problemów przekrojowych. Co najważniejsze, aplikacja w pełni wykorzystuje funkcje skalowalności i odporności dostępne na nowoczesnych platformach w chmurze.

### <a name="cloud-native-computing"></a>Przetwarzanie natywne dla chmury

Hmm... Po prostu użyliśmy terminu "*Cloud Native*". Najpierw pomyślałeś: "Co to dokładnie oznacza?" Innym buzzword przemysłu wymyślone przez dostawców oprogramowania na rynek więcej rzeczy?"

Na szczęście jest znacznie inaczej i miejmy nadzieję, że ta książka pomoże Cię przekonać.

W krótkim czasie natywna chmura stała się motorem napędowym w branży oprogramowania. Jest to nowy sposób myślenia o budowaniu dużych, złożonych systemów, podejście, które w pełni wykorzystuje nowoczesne praktyki tworzenia oprogramowania, technologie i infrastrukturę chmury. Podejście zmienia sposób projektowania, implementowania, wdrażania i operationalize systemów.

W przeciwieństwie do ciągłego szumu, który napędza naszą branżę, natywna chmura jest "*dla prawdziwych*". Rozważmy [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), konsorcjum ponad 300 dużych korporacji z karty do chmury natywnych przetwarzania wszechobecne w całej technologii i stosów chmury. Jako jedna z najbardziej wpływowych grup open source, obsługuje wiele najszybciej rozwijających się projektów open source w GitHub. Należą do nich projekty takie jak [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [Envoy](https://www.envoyproxy.io/)i [gRPC](https://grpc.io/).

CNCF wspiera ekosystem open-source i neutralności dostawców. Podążając za tym potencjalnym klientem, przedstawiamy natywne zasady chmury, wzorce i najlepsze rozwiązania, które są niezależne od technologii. Jednocześnie omówimy usługi i infrastrukturę dostępną w chmurze platformy Microsoft Azure do tworzenia systemów natywnych dla chmury.

Więc, co dokładnie jest Cloud Native? Usiądź wygodnie, zrelaksuj się i pomożemy Ci odkrywać ten nowy świat.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](definition.md)
