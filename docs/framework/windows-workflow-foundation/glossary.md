---
title: Słownik programu Windows Workflow Foundation dla programu .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
ms.openlocfilehash: 61d9acab1161302937e240eb8ebb506ca9f1585c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945629"
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a>Słownik programu Windows Workflow Foundation dla programu .NET Framework 4.5

Poniższe terminy są używane w dokumentacji programu Windows Workflow Foundation.

## <a name="terms"></a>Warunki

|Termin|Definicja|
|----------|----------------|
|aktywność|Jednostka zachowanie programu w programie Windows Workflow Foundation. Działania pojedynczego może składać się ze sobą w bardziej złożone działania.|
|Akcja działania|Struktura danych, używany do udostępnienia wywołania zwrotne do wykonania przepływu pracy i działania.|
|Argument|Definiuje przepływ danych do i z działania. Każdy argument ma określony kierunek: w, lub we/wy. Reprezentuje on danych wejściowych, wyjściowych i parametrów wejściowych/wyjściowych działania.|
|Zakładka|Punkt, w którym można wstrzymywać i poczekać na wznowienie działania.|
|Kompensacja|Grupa działania mające na celu cofnąć lub zminimalizować wpływ poprzednio ukończoną pracę.|
|Korelacja|Mechanizm służącą do rozesłania wiadomości do wystąpienia przepływu pracy lub usługi.|
|wyrażenie|Konstrukcja, która przyjmuje jeden lub więcej argumentów, wykonuje operację na argumenty i zwraca pojedynczą wartość. Wyrażenia może służyć wszędzie tam, gdzie działanie może być używane.|
|Schemat blokowy|Paradygmatu dobrze znanych modelowania reprezentuje składniki programu jako symbole połączone razem z strzałki kierunkowej.  W programie .NET Framework 4 przepływy pracy mogą być modelowane jako blokowe przy użyciu działania schematu blokowego.|
|długotrwałe procesu|Jednostka wykonywania programu, która nie zwraca niezwłocznie i może obejmować ponownego uruchomienia systemu.|
|trwałość|Zapisywanie stanu przepływu pracy lub usługa trwałego nośnika, aby może być zwolniony z pamięci lub odzyskany po awarii systemu.|
|automatu stanów|Paradygmatu dobrze znanych modelowania reprezentuje składniki programu jako poszczególnych stanów połączone razem z Stanami oparte na zdarzeniach.  Przepływy pracy mogą być modelowane jako maszyny stanu przy użyciu działania Automat stanów.|
|substancji|Reprezentuje grupę powiązanych zakładki w ramach wspólnego identyfikator i umożliwia środowiska uruchomieniowego do podejmowania decyzji o wznowienie zakładki w szczególności jest prawidłowy lub może stać się prawidłowe.|
|Konwertera typów|Typ CLR może być skojarzony z jedną lub więcej System.ComponentModel.TypeConverter pochodne typy, które włączają konwertowania wystąpienia typu CLR, do i z instancje innych typów. Konwertera typów jest skojarzony z typem CLR za pomocą atrybutu System.ComponentModel.TypeConverterAttribute.  Można określić TypeConverterAttribute bezpośrednio na typ CLR lub właściwość. Konwertera typów określony we właściwości zawsze mają pierwszeństwo przed konwertera typów określona dla typu CLR właściwości.|
|zmienna|Reprezentuje magazyn części danych, które muszą być zapisane i używane w dalszej części.|
|przepływ pracy|Pojedyncze działanie lub drzewa działania wywoływane przez proces hosta.|
|XAML|eXtensible Application Markup Language|
