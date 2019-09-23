---
title: Porównanie architektury ASP.NET Web Forms i Blazor
description: Dowiedz się, jak architektury ASP.NET Web Forms i Blazor Compare.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 1137218e1cd99a39240592be415f734223e90b77
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183960"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a>Porównanie architektury ASP.NET Web Forms i Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Chociaż ASP.NET Web Forms i Blazor mają wiele podobnych koncepcji, istnieją różnice w sposobie ich działania. Ten rozdział analizuje wewnętrzne działania i architektury ASP.NET Web Forms i Blazor.

## <a name="aspnet-web-forms"></a>Formularze sieci Web ASP.NET

Struktura formularzy sieci Web ASP.NET jest oparta na architekturze zorientowanej na strony. Każde żądanie HTTP dotyczące lokalizacji w aplikacji jest oddzielną stroną, z którą ASP.NET odpowiada. Po zażądaniu stron zawartość przeglądarki jest zastępowana wynikami żądanego strony.

Strony składają się z następujących składników:

* Znaczniki HTML
* C#lub kod Visual Basic
* Klasy związane z kodem zawierające funkcje logiki i obsługi zdarzeń
* Formanty

Formanty to jednostki interfejsu użytkownika sieci Web wielokrotnego użytku, które mogą być programowo umieszczane i współpracujące ze sobą na stronie. Strony składają się z plików kończących się na *. aspx* zawierających znaczniki, kontrolki i kod. Klasy związane z kodem znajdują się w plikach o tej samej nazwie podstawowej i rozszerzeniu *. aspx.cs* lub *. aspx. vb* , w zależności od używanego języka programowania. W interesującej sytuacji serwer sieci Web interpretuje zawartość plików *. aspx* i kompiluje je przy każdej zmianie. Ta ponowna kompilacja występuje nawet wtedy, gdy serwer sieci Web jest już uruchomiony.

Formanty mogą być kompilowane przy użyciu znaczników i dostarczanych jako kontrolki użytkownika. Kontrolka użytkownika pochodzi z `UserControl` klasy i ma podobną strukturę do strony. Znaczniki dla kontrolek użytkownika są przechowywane w pliku *. ascx* . Towarzysząca Klasa znajdująca się w kodzie znajduje się w pliku *. ascx.cs* lub *. ascx. vb* . Kontrolki można także kompilować całkowicie przy użyciu kodu, dziedzicząc z `WebControl` klasy podstawowej lub. `CompositeControl`

Strony mają również rozległy cykl życia zdarzeń. Każda Strona zgłasza zdarzenia dla zdarzeń inicjalizacji, ładowania, wyprerender i zwolnienia, które występują, gdy środowisko uruchomieniowe ASP.NET wykonuje kod strony dla każdego żądania.

Kontrolki na stronie są zwykle umieszczane na tej samej stronie, która przedstawiła formant i przenoszą razem z nimi ładunek z pola ukrytego formularza o nazwie `ViewState`. `ViewState` Pole zawiera informacje o stanie kontrolek w czasie, gdy zostały renderowane i przedstawione na stronie, co umożliwia środowisko uruchomieniowe ASP.NET w celu porównania i identyfikowania zmian zawartości przesłanej do serwera.

## <a name="blazor"></a>Blazor

Blazor to struktura interfejsu użytkownika sieci Web po stronie klienta podobna do platformy języka JavaScript, w której znajdują się środowiska frontonu, takie jak elementy kątowe lub reagowanie. Blazor obsługuje interakcje użytkowników i renderuje niezbędne aktualizacje interfejsu użytkownika. Blazor *nie jest* oparta na modelu żądanie-odpowiedź. Interakcje użytkownika są obsługiwane jako zdarzenia, które nie znajdują się w kontekście określonego żądania HTTP.

Aplikacje Blazor składają się z jednego lub większej liczby składników głównych, które są renderowane na stronie HTML.

![Składniki Blazor w kodzie HTML](./media/architecture-comparison/blazor-components-in-html.png)

Sposób, w jaki użytkownik określa, gdzie mają być renderowane składniki, oraz jak są rozłączone składniki, aby Interakcje użytkownika były [hostem](hosting-models.md) specyficznym dla modelu.

[Składniki](components.md) Blazor są klasami .NET, które reprezentują element interfejsu użytkownika wielokrotnego użytku. Każdy składnik utrzymuje własny stan i określa własną logikę renderowania, która może obejmować renderowanie innych składników. Składniki określają programy obsługi zdarzeń dla konkretnych interakcji użytkowników w celu zaktualizowania stanu składnika.

Gdy składnik obsługuje zdarzenie, Blazor renderuje składnik i śledzi zmiany w renderowanych danych wyjściowych. Składniki nie są renderowane bezpośrednio do Document Object Model (DOM). Zamiast tego są one renderowane do reprezentacji w pamięci modelu dom o nazwie `RenderTree` a, tak aby Blazor można było śledzić zmiany. Blazor porównuje nowo renderowane dane wyjściowe z poprzednimi danymi wyjściowymi, aby obliczyć różnice między interfejsem użytkownika, który następnie jest wydajnie stosowany do modelu DOM.

![Blazor DOM](./media/architecture-comparison/blazor-dom-interaction.png)

Składniki mogą również ręcznie wskazywać, że powinny być renderowane, jeśli ich stan zmieni się poza normalnym zdarzeniem interfejsu użytkownika. Blazor używa w `SynchronizationContext` celu wymuszenia pojedynczego wątku logicznego wykonywania. W tym `SynchronizationContext`przypadku są wykonywane metody cyklu życia składnika i wszystkie wywołania zwrotne zdarzeń wywoływane przez Blazor.

>[!div class="step-by-step"]
>[Poprzedni](introduction.md)
>[Następny](hosting-models.md)
