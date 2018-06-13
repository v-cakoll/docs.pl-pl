---
title: Architektura Mikrousług
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Architektura Mikrousług
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 9bcaacce323ed9afa482660f409312f9a1b82cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576484"
---
# <a name="microservices-architecture"></a>Architektura Mikrousług

Jak wskazuje nazwę, architektura mikrousług jest podejście do tworzenia aplikacji serwera jako zestaw usług mała. Każda usługa jest uruchamiana we własnym procesie i komunikuje się z innymi procesami przy użyciu protokołów, takich jak HTTP/HTTPS, Websocket, lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Każdy mikrousługi implementuje określonej domeny end-to-end lub możliwości biznesowe w obrębie granicy kontekstu oraz poszczególnych musi być opracowana autonomicznie i możliwych do wdrożenia niezależnie. Na koniec każdego mikrousługi powinien być właścicielem jego modelu danych powiązanych domeny i logika domeny (suwerenności i zarządzanie zdecentralizowane danych) na podstawie technologii magazynowania danych (SQL, NoSQL) i różnych języków programowania.

Jaki rozmiar powinna być mikrousługi? Podczas tworzenia mikrousługi, rozmiar nie może być istotne. Zamiast tego istotne należy utworzyć słabo sprzężona usług, więc autonomię tworzenia, wdrażania i skalowania dla każdej usługi. Oczywiście podczas identyfikacji i mikrousług projektowania, należy spróbować były możliwie najmniejsze tak długo, jak nie ma zbyt wiele zależności bezpośrednich z innych mikrousług. Większe znaczenie niż rozmiar mikrousługi spójności wewnętrznego, który musi mieć i jego niezależność od innych usług.

Dlaczego architektura mikrousług? Krótko mówiąc zapewnia elastyczność długoterminowej. Mikrousług włączyć lepsze utrzymanie w systemach złożonych, duże i wysoko skalowane przez umożliwienie tworzenia aplikacji z wielu usług niezależnie do wdrożenia że mieć cykle szczegółowego i autonomicznego.

Dodatkowa korzyść mikrousług można skalować w poziomie niezależnie. Zamiast aplikacją wbudowanymi pojedynczego musi skalowanie w poziomie jako jednostki, możesz zamiast tego skalować w poziomie określonych mikrousług. W ten sposób można skalować tylko funkcjonalności wymaga więcej przetwarzania zasilania lub sieci przepustowość do obsługi żądanie, a nie skalowania innych obszarach aplikacji, które nie muszą być skalowane obszaru. Oznacza to, że oszczędności, ponieważ potrzebna mniej sprzętu.

![](./media/image6.png)

**Rysunek 4 – 6**. Wbudowanymi wdrożenia i podejście mikrousług

Jak pokazano na rysunku 4 – 6, podejście mikrousług umożliwia elastyczne zmiany i szybkie iteracji każdego mikrousługi nie można zmienić określone, mała obszary aplikacji złożonych, duże i skalowalne.

Zaprojektowanie szczegółowych aplikacji opartych na mikrousług umożliwia ciągłej integracji i rozwiązań ciągłego dostarczania. Przyspiesza również dostarczania nowych funkcji, do aplikacji. Szczegółowe kompozycji aplikacji umożliwia również uruchamianie i testowanie mikrousług w izolacji i rozwijać je samodzielnie, przy zachowaniu wyczyść kontraktów między nimi. Tak długo, jak nie zmienisz interfejsów lub umowy, można zmienić wewnętrzny wykonania dowolnego mikrousługi lub dodawanie nowych funkcji bez przerywania innych mikrousług.

Poniżej przedstawiono istotne aspekty umożliwiające Powodzenie w przejściu w środowisku produkcyjnym z użyciem systemu mikrousług:

-   Monitorowanie i kondycji kontroli usług i infrastruktury.

-   Skalowalnej infrastruktury usług (czyli chmury i orchestrators).

-   Zabezpieczenia projektowania i wdrażania na wielu poziomach: uwierzytelniania, autoryzacji, zarządzanie klucze tajne, bezpiecznej komunikacji, itp.

-   Dostarczanie szybkie aplikacji, zwykle za pomocą różnych zespołów koncentrujących się na różnych mikrousług.

-   DevOps i CI/CD rozwiązań i infrastruktury.

Z nich tylko pierwsze trzy są objęte lub wprowadzone w tym przewodniku. Ostatnie dwa punkty, które są związane z cyklem życia aplikacji, znajdują się w dodatkowych [konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami](https://aka.ms/dockerlifecycleebook) Książka elektroniczna.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Russinovichem znaku. Mikrousług: Ma obrotów aplikacji obsługiwane przez usługę w chmurze**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Pole Fowler. Mikrousług**
    [*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)

-   **Pole Fowler. Wymagania wstępne Mikrousługi**
    [*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson. Bryłkach chmury obliczeniowej**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Torre de la Cesarowi. Konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami** (do pobrania Książka elektroniczna) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[Poprzednie] (usługa ukierunkowane architecture.md) [dalej] (danych suwerenności na microservice.md)
