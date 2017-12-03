---
title: "Słownik programu Windows Workflow Foundation dla programu .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
caps.latest.revision: "259"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1153b1b87a7b16c330d05a6a89516ab1944bf6e1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a>Słownik programu Windows Workflow Foundation dla programu .NET Framework 4.5
Poniższe terminy są używane w dokumentacji systemu Windows Workflow Foundation.  
  
## <a name="terms"></a>Warunki  
  
|Termin|Definicja|  
|----------|----------------|  
|aktywność|Jednostka zachowanie programu w programie Windows Workflow Foundation. Pojedynczego działania może składać się ze sobą w bardziej złożonych działania.|  
|Akcja działania|Struktura danych używany do udostępnienia wywołań zwrotnych do wykonania przepływu pracy i działania.|  
|Argument|Definiuje przepływ danych do i z działania. Każdy argument ma kierunek określony: w, out lub we/wy. Reprezentuje tych danych wejściowych, wyjściowych i parametry wejścia/wyjścia aktywności.|  
|Zakładka|Punkt, jaką można wstrzymywać i poczekaj, aby można wznowić działania.|  
|kompensacji|Grupa działania mające na celu cofnąć lub ograniczyć wpływ poprzednio ukończoną pracę.|  
|korelacji|Mechanizm do rozesłania wiadomości do wystąpienia przepływu pracy lub usługi.|  
|wyrażenie|Konstrukcja, która przyjmuje jeden lub więcej argumentów wykonuje operację na argumenty i zwraca pojedynczą wartość. Można użyć wyrażeń wszędzie tam, gdzie działanie może być używane.|  
|Schemat blokowy|Modelu dobrze znanego modelowania, który reprezentuje składniki programu jako symbole połączone razem z strzałki kierunkowej.  W .NET Framework 4 przepływy pracy mogą być modelowane jako blokowych za pomocą działania Flowchart.|  
|długotrwałe procesu|Jednostka wykonania programu, nie zwracać natychmiast, który może obejmować ponownego uruchomienia systemu.|  
|trwałość|Zapisywanie stanu przepływu pracy lub usługi trwałego nośnika, tak aby było zwolniona z pamięci lub odzyskany po awarii systemu.|  
|Komputer stanu|Model dobrze znanego modelowania reprezentująca składniki programu jako poszczególnych stanów połączone razem z przejść stanu sterowanego zdarzeniami.  Przepływy pracy mogą być modelowane jako za pomocą działania StateMachine maszyny stanu.|  
|substancja|Reprezentuje grupę powiązanych zakładek w obszarze identyfikator wspólnej i umożliwia podejmowanie decyzji o jest nieprawidłowa lub może stać się prawidłowe wznowienie zakładki określonego środowiska uruchomieniowego.|  
|Konwerter typów|Typu CLR może być skojarzony z jedną lub więcej System.ComponentModel.TypeConverter typów, umożliwiających konwertowania wystąpienia typu CLR do i z wystąpień innych typów pochodnych. Converterr typu jest skojarzony z typem CLR za pomocą atrybutu System.ComponentModel.TypeConverterAttribute.  Można określić TypeConverterAttribute bezpośrednio na typ CLR lub właściwości. Konwerter typu określony we właściwości zawsze mają pierwszeństwo przed konwertera typów określonych w typie CLR właściwości.|  
|zmienna|Reprezentuje magazyn niektórych danych, który musi być zapisany i dostęp do później.|  
|przepływ pracy|Pojedyncze działanie lub drzewa działania wywoływane przez proces hosta.|  
|XAML|eXtensible Application Markup Language|
