---
title: Opcje tworzenia działań w WF
ms.date: 03/30/2017
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
ms.openlocfilehash: 219d759cd1390a83abfb90af509b21047085f6e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774234"
---
# <a name="activity-authoring-options-in-wf"></a>Opcje tworzenia działań w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] zapewnia kilka opcji tworzenia działań niestandardowych. Prawidłowe metody służące do tworzenia danego działania, zależy od tego, jakie funkcje środowiska wykonawczego są wymagane.  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>Przy wyborze rozwiązania, które podstawowego elementu Activity klasy do użycia na potrzeby tworzenia działań niestandardowych  
 W poniższej tabeli wymieniono funkcje dostępne w klasach bazowych działań niestandardowych.  
  
|Klasa podstawowego elementu activity|Dostępne funkcje|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|Redaguj grupami dostarczane przez system i niestandardowych działań do działań złożonych.|  
|<xref:System.Activities.CodeActivity>|Implementuje funkcje imperatywnego, zapewniając <xref:System.Activities.CodeActivity%601.Execute%2A> metodę, która może zostać zastąpiona. Umożliwia również dostęp do śledzenia, zmienne i argumenty...|  
|<xref:System.Activities.NativeActivity>|Zawiera wszystkie funkcje <xref:System.Activities.CodeActivity>, a także Trwa przerywanie wykonywania działania, który anulował wykonanie działania podrzędne, korzystanie z zakładek i Planowanie działań, działanie akcje i funkcje.|  
|<xref:System.Activities.DynamicActivity>|Zapewnia podejście podobne do modelu DOM do tworzenia działań, które interfejsy za pomocą projektanta WF i maszyny czasu wykonywania za pomocą <xref:System.ComponentModel.ICustomTypeDescriptor>, dzięki czemu nowe działania, które ma zostać utworzony bez definiowania nowych typów.|  
  
## <a name="authoring-activities-using-activity"></a>Tworzenie działań przy użyciu działania  
 Działania, które wynikają z <xref:System.Activities.Activity> compose funkcji przez łączenie innych istniejących działań. Te działania mogą być niestandardowe istniejących działań i działania z [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] biblioteki działań. Złożenia te działania to najprostszy sposób tworzenia funkcji niestandardowych. To podejście jest najczęściej zajęta, podczas tworzenia przepływów pracy przy użyciu środowiska projektowania wizualnego.  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>Tworzenie działań przy użyciu elementu CodeActivity lub AsyncCodeActivity  
 Działania, które wynikają z <xref:System.Activities.CodeActivity> lub <xref:System.Activities.AsyncCodeActivity> można zaimplementować imperatywne funkcji przez zastąpienie <xref:System.Activities.CodeActivity%601.Execute%2A> metody za pomocą niestandardowego kodu imperatywnego. Niestandardowy kod jest wykonywany, gdy działanie jest wykonywany przez środowisko uruchomieniowe. Podczas działania utworzone w ten sposób mają dostęp do funkcji niestandardowych, mogą nie mają dostęp do wszystkich funkcji środowiska uruchomieniowego, takie jak pełny dostęp do środowiska wykonania, możliwość zaplanowania działania podrzędne, tworzenia zakładek lub obsługa Anulowanie lub przerywania metody. Gdy <xref:System.Activities.CodeActivity> jest wykonywana, ma dostęp do skrócona wersja środowiska wykonawczego (za pośrednictwem <xref:System.Activities.CodeActivityContext> lub <xref:System.Activities.AsyncCodeActivityContext> klasy). Działania utworzone za pomocą <xref:System.Activities.CodeActivity> mają dostęp do rozpoznawania argumentów i zmiennych, rozszerzenia oraz śledzenie. Planowanie działań asynchronicznych może odbywać się przy użyciu <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="authoring-activities-using-nativeactivity"></a>Tworzenie działań przy użyciu klasy NativeActivity  
 Działań, które wynikają z <xref:System.Activities.NativeActivity>, podobne do tych, które wynikają z <xref:System.Activities.CodeActivity>, utworzenia imperatywne funkcji przez zastąpienie <xref:System.Activities.NativeActivity.Execute%2A>, również ma dostęp do wszystkich funkcji środowiska wykonawczego przepływów pracy za pośrednictwem <xref:System.Activities.NativeActivityContext> , które pobiera przekazany do <xref:System.Activities.NativeActivity.Execute%2A> metody. Ten kontekst zapewnia obsługę planowania i anulowanie działania podrzędne, wykonywanie <xref:System.Activities.ActivityAction> i <xref:System.Activities.ActivityFunc%601> obiektów, przepływy transakcji do przepływu pracy, wywoływanie asynchronicznych procesów, anulowanie i Przerywanie wykonywania, dostęp do wykonania właściwości i rozszerzeń i zakładek (uchwytów wznawianie wstrzymanej przepływów pracy).  
  
## <a name="authoring-activities-using-dynamicactivity"></a>Tworzenie działań przy użyciu działania DynamicActivity  
 W przeciwieństwie do innych trzy typy działań, nowa funkcja nie jest tworzony przez wyprowadzanie nowych typów z <xref:System.Activities.DynamicActivity> (klasa jest zapieczętowany,), ale zamiast tego złożenia funkcji do <xref:System.Activities.DynamicActivity.Properties%2A> i <xref:System.Activities.DynamicActivity.Implementation%2A> właściwości za pomocą działania dokumentu Object model (DOM).  
  
## <a name="authoring-activities-that-return-a-result"></a>Tworzenie działań, które zwracają wynik  
 Wiele działań musi zwrócić wynik po ich wykonaniu. Chociaż istnieje możliwość zawsze Definiowanie niestandardowego <xref:System.Activities.OutArgument%601> w ramach działania w tym celu zaleca się użyć zamiast tego <xref:System.Activities.Activity%601>, lub pochodzić od <xref:System.Activities.CodeActivity%601> lub <xref:System.Activities.NativeActivity%601>. Każda z tych klas bazowych ma <xref:System.Activities.OutArgument%601> o nazwie wynik, używanego przez swoje działania do jego zwracanej wartości. Działania, które zwracają wynik powinien być używany tylko, jeśli tylko jeden wynik musi zostać zwrócone przez działanie; Jeśli potrzebujesz wielu wyników do zwrócenia, oddziel <xref:System.Activities.OutArgument%601> elementów członkowskich, które powinny być używane zamiast tego.
