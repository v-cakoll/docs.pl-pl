---
title: Wyznaczanie zakresu i widoczność definicji działania
ms.date: 03/30/2017
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
ms.openlocfilehash: 27c43323a176c841f3d90cb9c52f25599bc0686d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976693"
---
# <a name="activity-definition-scoping-and-visibility"></a>Wyznaczanie zakresu i widoczność definicji działania
Działanie definicji zakresu i widoczność, podobnie jak wyznaczanie zakresu i widoczność obiektu, jest możliwość dostęp do elementów członkowskich działanie innych obiektów lub działań. Definicja działanie odbywa się przez następujące implementacje:  
  
1. Określanie elementów członkowskich (<xref:System.Activities.Argument>, <xref:System.Activities.Variable>, i <xref:System.Activities.ActivityDelegate> obiektów i działania podrzędne) udostępnia działanie w swoim użytkownikom.  
  
2. Implementowanie logiki wykonywania działania  
  
 Implementacja może obejmować elementy członkowskie, które nie są widoczne dla konsumentów, działania, ale są raczej szczegóły implementacji.  Podobnie jak w definicji typu, model działania umożliwia autorowi kwalifikowania widoczność elementu członkowskiego działań dotyczących definicji działania zostały zdefiniowane.  Ten widoczność reguluje aspekty użycia elementu członkowskiego, takie jak zakresu danych.  
  
## <a name="scope"></a>Zakres  
 Oprócz określania zakresu danych, działania modelu widoczność można ograniczyć dostęp do innych aspektów działalności, takich jak sprawdzanie poprawności, debugowanie, śledzenie lub śledzenia. Właściwości wykonania za pomocą widoczności i określania zakresu ograniczać wykonywania do określonego zakresu definicji. Dodatkowych katalogów głównych umożliwia widoczności i określać ich zakresy Państwo przechwycona przez ograniczenie <xref:System.Activities.Statements.CompensableActivity> do zakresu definicji, w którym kompensacyjne działania są używane.  
  
## <a name="definition-and-usage"></a>Definiowanie i używanie  
 Przepływ pracy jest napisany przez dziedziczenie z klasy bazowej działania i za pomocą działania programu, tworząc nowe działania [wbudowana biblioteka działań](net-framework-4-5-built-in-activity-library.md). Aby można było użyć działania, autor działania należy skonfigurować widoczność każdego składnika jego definicji.  
  
### <a name="activity-members"></a>Działania elementów członkowskich  
 Model działania definiuje argumentów, zmienne, delegaty i działania podrzędne, które działania sprawia, że dostępne dla klientów. Każda z tych elementów członkowskich mogą być deklarowane jako `public` lub `private`. Publiczne elementy członkowskie są konfigurowane przez konsumenta aktywności, natomiast `private` członkowie korzystać z implementacją rozwiązane przez autora działania. Reguły widoczności danych określania zakresu są następujące:  
  
1. Publiczne elementy członkowskie i publiczne elementy członkowskie działania podrzędne publicznych odwoływać się do publicznego zmiennych.  
  
2. Składowe prywatne i publiczne elementy członkowskie działania podrzędne publiczne można odwoływać się do argumentów i zmiennych prywatnych.  
  
 Element członkowski, który można ustawić przez konsumenta działanie nigdy nie powinno się prywatnych.  
  
### <a name="authoring-models"></a>Tworzenie modeli  
 Działania niestandardowe są zdefiniowane przy użyciu <xref:System.Activities.NativeActivity>, <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, lub <xref:System.Activities.AsyncCodeActivity>. Działania, które wynikają z tych klas można ujawnić typy inny element członkowski z różne widoczności.  
  
#### <a name="nativeactivity"></a>Klasy NativeActivity  
 Działania, które wynikają z <xref:System.Activities.NativeActivity> zachowanie, który został napisany w kodu imperatywnego i opcjonalnie można zdefiniować przy użyciu istniejących działań. Wyprowadzanie działania z <xref:System.Activities.NativeActivity> nieograniczony dostęp do wszystkich funkcji udostępnianych przez środowisko uruchomieniowe. Każdy członek takie działanie można zdefiniować przy użyciu widoczność publiczne lub prywatne, z wyjątkiem argumentów, które mogą być deklarowane tylko jako `public`.  
  
 Elementy członkowskie klas pochodnych <xref:System.Activities.NativeActivity> są zadeklarowane za pomocą środowiska uruchomieniowego <xref:System.Activities.NativeActivityMetadata> struktury przekazany do <xref:System.Activities.NativeActivity.CacheMetadata%2A> metody.  
  
#### <a name="activity"></a>Działanie  
 Działania utworzone za pomocą <xref:System.Activities.Activity> zachowanie, przeznaczoną wyłącznie poprzez tworzenie innych działań. <xref:System.Activities.Activity> Klasa ma jedno działanie podrzędne wdrożenia, można uzyskać za pomocą środowiska uruchomieniowego <xref:System.Activities.Activity.Implementation%2A>. Działania, wynikające z <xref:System.Activities.Activity> można zdefiniować argumenty publiczny, publiczny zmienne, ActivityDelegates importowanych i importowanych działań.  
  
 Zaimportowane ActivityDelegates działań są deklarowane jako publiczne elementy podrzędne działania, ale nie można zaplanować bezpośrednio przez działanie. Te informacje są używane podczas sprawdzania poprawności, aby zapobiegać uruchamianiu jej skierowaną do nadrzędnego operacji sprawdzania poprawności w lokalizacjach, w których nigdy nie będą wykonywane działania. Ponadto zaimportowane elementy podrzędne, podobnie jak publiczne elementy podrzędne, można odwołanie i zaplanować przy wdrażaniu tego działania. Oznacza to, że może zawierać działanie, które importuje działania o nazwie działania Activity1 <xref:System.Activities.Statements.Sequence> w jej wdrożenia, które planuje działania Activity1.  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity / AsyncCodeActivity  
 Ta klasa bazowa jest używany do tworzenia zachowanie kodu imperatywnego. Działania, które pochodzą z tej klasy mają tylko dostęp do argumentów, które udostępniają. Oznacza to, że tylko elementy członkowskie, które można uwidocznić te działania są publiczne argumentów. Nie ma innych członków lub widoczności mają zastosowanie do tych działań.  
  
#### <a name="summary-of-visibilities"></a>Podsumowanie widoczności  
 Poniższa tabela zawiera podsumowanie informacji o wcześniej w tej sekcji.  
  
|Typ elementu członkowskiego|Klasy NativeActivity|Działanie|CodeActivity / AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|Argumenty|Publiczny / prywatny|Public|Nie dotyczy|  
|Zmienne|Publiczny / prywatny|Public|Nie dotyczy|  
|Działania podrzędne|Publiczny / prywatny|Publiczne, jeden problem rozwiązany prywatnej podrzędnego, zdefiniowane w implementacji.|Nie dotyczy|  
|ActivityDelegates|Publiczny / prywatny|Public|Nie dotyczy|  
  
 Ogólnie rzecz biorąc element członkowski, który nie można ustawić przez konsumenta działania nie należy publicznych.  
  
### <a name="execution-properties"></a>Właściwości wykonania  
 W niektórych przypadkach warto ograniczyć zakres do publicznych elementów podrzędnych działania właściwości wykonania określonego. <xref:System.Activities.ExecutionProperties> Kolekcji zapewnia tę funkcję za pomocą <xref:System.Activities.ExecutionProperties.Add%2A> metody. Ta metoda ma parametrów typu Boolean wskazującą, czy określona właściwość obejmuje wszystkie obiekty podrzędne lub tylko te, które są publiczne. Jeśli ten parametr jest równa `true`, właściwość będzie widoczny tylko publiczne elementy członkowskie i publiczne elementy członkowskie publicznych dzieci.  
  
### <a name="secondary-roots"></a>Dodatkowych katalogów głównych  
 Pomocniczy główny jest w środowisku uruchomieniowym wewnętrzny mechanizm zarządzania stanem działań wynagrodzenia. Gdy <xref:System.Activities.Statements.CompensableActivity> zakończył uruchomiona, jego stan nie są czyszczone natychmiast. Zamiast tego stanu jest obsługiwana przez środowiska uruchomieniowego w głównym pomocniczej przed ukończeniem odcinek wynagrodzenia. W środowiskach lokalizacji przechwycić przy użyciu dodatkowej głównego odpowiadają zakresu definicji, w którym jest używane działanie kompensacyjne.
