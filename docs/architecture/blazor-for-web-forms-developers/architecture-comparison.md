---
title: Porównanie architektury formularzy sieci Web ASP.NET iBlazor
description: Dowiedz się, jak architektury ASP.NET Web Forms i Blazor Compare.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 51b114c842e131ad9b9a589bf5137a522e135082
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173435"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a>Porównanie architektury formularzy sieci Web ASP.NET iBlazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Chociaż ASP.NET formularze sieci Web i Blazor mają wiele podobnych koncepcji, istnieją różnice w sposobie ich działania. Ten rozdział analizuje wewnętrzne działania i architektury formularzy sieci Web ASP.NET oraz Blazor .

## <a name="aspnet-web-forms"></a>Formularze sieci Web ASP.NET

Struktura formularzy sieci Web ASP.NET jest oparta na architekturze zorientowanej na strony. Każde żądanie HTTP dotyczące lokalizacji w aplikacji jest oddzielną stroną, z którą ASP.NET odpowiada. Po zażądaniu stron zawartość przeglądarki jest zastępowana wynikami żądanego strony.

Strony składają się z następujących składników:

- Znaczniki HTML
- Kod w języku C# lub Visual Basic
- Klasy związane z kodem zawierające funkcje logiki i obsługi zdarzeń
- Formanty

Formanty to jednostki interfejsu użytkownika sieci Web wielokrotnego użytku, które mogą być programowo umieszczane i współpracujące ze sobą na stronie. Strony składają się z plików kończących się na *. aspx* zawierających znaczniki, kontrolki i kod. Klasy związane z kodem znajdują się w plikach o tej samej nazwie podstawowej i rozszerzeniu *. aspx.cs* lub *. aspx. vb* , w zależności od używanego języka programowania. W interesującej sytuacji serwer sieci Web interpretuje zawartość plików *. aspx* i kompiluje je przy każdej zmianie. Ta ponowna kompilacja występuje nawet wtedy, gdy serwer sieci Web jest już uruchomiony.

Formanty mogą być kompilowane przy użyciu znaczników i dostarczanych jako kontrolki użytkownika. Kontrolka użytkownika pochodzi z `UserControl` klasy i ma podobną strukturę do strony. Znaczniki dla kontrolek użytkownika są przechowywane w pliku *. ascx* . Towarzysząca Klasa znajdująca się w kodzie znajduje się w pliku *. ascx.cs* lub *. ascx. vb* . Kontrolki można także kompilować całkowicie przy użyciu kodu, dziedzicząc z `WebControl` `CompositeControl` klasy podstawowej lub.

Strony mają również rozległy cykl życia zdarzeń. Każda Strona zgłasza zdarzenia dla zdarzeń inicjalizacji, ładowania, wyprerender i zwolnienia, które występują, gdy środowisko uruchomieniowe ASP.NET wykonuje kod strony dla każdego żądania.

Kontrolki na stronie są zwykle umieszczane na tej samej stronie, która przedstawiła formant i przenoszą razem z nimi ładunek z pola ukrytego formularza o nazwie `ViewState` . `ViewState`Pole zawiera informacje o stanie kontrolek w czasie, gdy zostały renderowane i przedstawione na stronie, co umożliwia środowisko uruchomieniowe ASP.NET w celu porównania i identyfikowania zmian zawartości przesłanej do serwera.

## Blazor

Blazorjest strukturą internetowego interfejsu użytkownika po stronie klienta podobną do platformy języka Java frontonu, takiej jak kątowy lub reaguje. Blazorobsługuje Interakcje użytkownika i renderuje niezbędne aktualizacje interfejsu użytkownika. Blazor*nie* bazuje na modelu typu żądanie-odpowiedź. Interakcje użytkownika są obsługiwane jako zdarzenia, które nie znajdują się w kontekście określonego żądania HTTP.

Blazoraplikacje składają się z jednego lub większej liczby składników głównych, które są renderowane na stronie HTML.

![Blazorskładniki w kodzie HTML](./media/architecture-comparison/blazor-components-in-html.png)

Sposób, w jaki użytkownik określa, gdzie mają być renderowane składniki, oraz jak są rozłączone składniki, aby Interakcje użytkownika były [hostem](hosting-models.md) specyficznym dla modelu.

Blazor[składniki](components.md) to klasy .NET, które reprezentują element interfejsu użytkownika wielokrotnego użytku. Każdy składnik utrzymuje własny stan i określa własną logikę renderowania, która może obejmować renderowanie innych składników. Składniki określają programy obsługi zdarzeń dla konkretnych interakcji użytkowników w celu zaktualizowania stanu składnika.

Gdy składnik obsługuje zdarzenie, Blazor renderuje składnik i śledzi zmiany w renderowanych danych wyjściowych. Składniki nie są renderowane bezpośrednio do Document Object Model (DOM). Zamiast tego renderuje do reprezentacji w pamięci modelu DOM o nazwie a, `RenderTree` Aby Blazor można było śledzić zmiany. Blazorporównuje nowo renderowane dane wyjściowe z poprzednimi danymi wyjściowymi w celu obliczenia różnic między interfejsem użytkownika, który następnie jest wydajnie stosowany do modelu DOM.

![BlazorInterakcja DOM](./media/architecture-comparison/blazor-dom-interaction.png)

Składniki mogą również ręcznie wskazywać, że powinny być renderowane, jeśli ich stan zmieni się poza normalnym zdarzeniem interfejsu użytkownika. Blazorużywa `SynchronizationContext` do wymuszania pojedynczego wątku logicznego wykonywania. Metody cyklu życia składnika i wszelkie wywołania zwrotne zdarzeń, które są wywoływane przez Blazor są wykonywane na tym serwerze `SynchronizationContext` .

>[!div class="step-by-step"]
>[Poprzedni](introduction.md) 
> [Dalej](hosting-models.md)
