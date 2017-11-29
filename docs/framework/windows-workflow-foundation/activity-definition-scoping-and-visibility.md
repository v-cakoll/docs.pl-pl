---
title: "Określanie zakresu definicji działania i widoczność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 478dc783f5bb80283e431817433616b4bdada099
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="activity-definition-scoping-and-visibility"></a>Określanie zakresu definicji działania i widoczność
Zakresu definicji działania i widoczność, podobnie jak zakres i widoczność obiektu, jest możliwość dostęp do elementów członkowskich działanie innych obiektów lub działania. Definicja aktywności jest wykonywane przez implementacje następujące:  
  
1.  Określanie elementów członkowskich (<xref:System.Activities.Argument>, <xref:System.Activities.Variable>, i <xref:System.Activities.ActivityDelegate> obiektów i działań podrzędnych) działanie udostępnia swoim użytkownikom.  
  
2.  Implementowanie logiki wykonywania działania  
  
 Implementacja może obejmować elementów członkowskich, które nie są widoczne dla użytkowników, działania, ale są raczej szczegóły implementacji.  Podobnie jak w definicji typu, model aktywności umożliwia autorowi zakwalifikować widoczność elementu członkowskiego działania dotyczące definicji działania definiowanego.  Ta widoczność reguluje aspektów użycia elementów członkowskich, takich jak zakresy danych.  
  
## <a name="scope"></a>Zakres  
 Oprócz zakresu danych, widoczność modelu działania można ograniczyć dostęp do innych aspektów działalności, takich jak sprawdzanie poprawności, debugowanie, śledzenie i dane śledzenia. Właściwości wykonania za pomocą widoczność i określania zakresu dla ograniczający wykonywania do określonego zakresu definicji. Dodatkowej katalogów głównych umożliwia widoczności i określania zakresu ograniczyć stanu przechwycone przez <xref:System.Activities.Statements.CompensableActivity> do zakresu definicji, w którym compensable działania są używane.  
  
## <a name="definition-and-usage"></a>Definicja i użycia  
 Przepływ pracy została napisana przez tworzenie nowych działań przez dziedziczenie z klas działanie podstawowe i przy użyciu działań [Biblioteka działań wbudowanych](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). Aby można było użyć działania, określony przez autora działania należy skonfigurować widoczność każdego składnika jego definicji.  
  
### <a name="activity-members"></a>Elementy członkowskie działania  
 Model aktywności definiuje argumenty, zmienne, delegatów i działania podrzędne, które udostępnia działania dla konsumentów. Każdy z tych elementów członkowskich mogą być deklarowane jako `public` lub `private`. Publiczne elementy członkowskie są konfigurowane przez konsumentów działania, podczas gdy `private` członków Użyj implementacji rozwiązany przez autora działania. Reguły widoczności dla zakresu danych są następujące:  
  
1.  Publiczne elementy członkowskie i publiczne elementy Członkowskie działań podrzędnych publicznego można odwoływać się do zmiennych publicznych.  
  
2.  Prywatne elementy członkowskie i publiczne elementy Członkowskie działań podrzędnych publicznego można odwoływać się do argumentów i zmiennych prywatnych.  
  
 Element członkowski, który można ustawić przez konsumenta działania nigdy nie powinno się prywatne.  
  
### <a name="authoring-models"></a>Tworzenie modeli  
 Zdefiniowano działania niestandardowe przy użyciu <xref:System.Activities.NativeActivity>, <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, lub <xref:System.Activities.AsyncCodeActivity>. Działaniach pochodzących z tych klas mogą uwidaczniać typów inny element członkowski o różne widoczności.  
  
#### <a name="nativeactivity"></a>Działania NativeActivity  
 Działania, które pochodzą z <xref:System.Activities.NativeActivity> zachowują się są zapisywane w kodzie imperatywnych, którą można opcjonalnie zdefiniować za pomocą istniejących działań. Wyprowadzanie działania z <xref:System.Activities.NativeActivity> nieograniczony dostęp do wszystkich funkcji udostępnianych przez środowisko uruchomieniowe. Każdy członek takie działanie można zdefiniować przy użyciu widoczność publicznych lub prywatnych, z wyjątkiem argumentów, które mogą być deklarowane tylko jako `public`.  
  
 Elementy członkowskie klas pochodnych <xref:System.Activities.NativeActivity> są zadeklarowane przy użyciu środowiska uruchomieniowego <xref:System.Activities.NativeActivityMetadata> struktury przekazany do <xref:System.Activities.NativeActivity.CacheMetadata%2A> — metoda.  
  
#### <a name="activity"></a>Działanie  
 Działania utworzone za pomocą <xref:System.Activities.Activity> zachowują się przeznaczony wyłącznie do tworzenia innych działań. <xref:System.Activities.Activity> Klasa ma jedno działanie podrzędne implementacji, można uzyskać za pomocą środowiska uruchomieniowego <xref:System.Activities.Activity.Implementation%2A>. Wyprowadzanie z działania <xref:System.Activities.Activity> można zdefiniować publicznego argumentów, zmiennych publicznych Activitydelegate zaimportowane i zaimportowanych działań.  
  
 Zaimportowane Activitydelegate i działania są deklarowane jako publicznych działaniach podrzędnych działania, ale nie można zaplanować bezpośrednio przez działanie. Te informacje jest używany podczas weryfikacji Aby zapobiegać uruchamianiu w lokalizacjach, w którym działanie nigdy nie zostanie wykonane sprawdzanie poprawności uwzględniającym działania nadrzędnego. Ponadto importowanych elementów podrzędnych, podobnie jak publicznych elementów podrzędnych, można odwołuje się do i zaplanowane przez implementację działania. Oznacza to, że działanie importującego działanie o nazwie działania Activity1 może zawierać <xref:System.Activities.Statements.Sequence> w jej wdrożenia, które planuje działania Activity1.  
  
#### <a name="codeactivity-asynccodeactivity"></a>Klasy CodeActivity / AsyncCodeActivity  
 Ta klasa podstawowa jest używany do tworzenia zachowanie w kodzie konieczne. Działania, które pochodzą z tej klasy mają tylko dostęp do argumentów, które udostępniają. Oznacza to, że tylko elementy członkowskie, które można ujawnić te działania są publiczne argumentów. Nie elementów członkowskich lub widoczności dotyczą te działania.  
  
#### <a name="summary-of-visibilities"></a>Podsumowanie widoczności  
 W poniższej tabeli przedstawiono informacje we wcześniejszej części tej sekcji.  
  
|Typ elementu członkowskiego|Działania NativeActivity|Działanie|Klasy CodeActivity / AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|Argumenty|Publiczny / prywatny|Public|Nie dotyczy|  
|Zmienne|Publiczny / prywatny|Public|Nie dotyczy|  
|Działania podrzędne|Publiczny / prywatny|Publiczne, jedną wyznaczonym prywatnej podrzędne zdefiniowane w implementacji.|Nie dotyczy|  
|Activitydelegate|Publiczny / prywatny|Public|Nie dotyczy|  
  
 Ogólnie rzecz biorąc elementu członkowskiego, który nie można ustawić przez konsumenta działania nie należy publicznego.  
  
### <a name="execution-properties"></a>Właściwości wykonania  
 W niektórych scenariuszach jest przydatne do określania zakresu wykonywania określonej właściwości na publicznych działaniach podrzędnych działania. <xref:System.Activities.ExecutionProperties> Kolekcji zapewnia tę funkcję z <xref:System.Activities.ExecutionProperties.Add%2A> metody. Ta metoda ma parametrów typu Boolean wskazującą, czy określona właściwość obejmuje wszystkie elementy podrzędne lub tylko te, które są publiczne. Jeśli ten parametr ma wartość `true`, właściwość będą widoczne tylko publiczne elementy członkowskie i publiczne elementy członkowskie swoich publicznych obiektach podrzędnych.  
  
### <a name="secondary-roots"></a>Pomocnicze certyfikaty główne  
 Dodatkowej główny jest wewnętrzny mechanizm środowiska uruchomieniowego zarządzania stan kompensacji działania. Gdy <xref:System.Activities.Statements.CompensableActivity> zakończył uruchomiona, jego stan nie są czyszczone natychmiast. Zamiast tego stanu jest obsługiwana przez środowisko uruchomieniowe w głównym dodatkowej dopiero po ukończeniu epizodu kompensacji. W środowiskach lokalizacji przechwytywane z głównym dodatkowej odpowiadają zakres definicji, w którym jest używana Compensable działania.
