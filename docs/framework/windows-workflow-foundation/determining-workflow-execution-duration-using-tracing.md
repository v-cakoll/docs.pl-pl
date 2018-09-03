---
title: Określanie czasu trwania wykonania przepływu pracy za pomocą śledzenia
ms.date: 03/30/2017
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
ms.openlocfilehash: c51fdf4543939fc068092b84e02eeb5f52e77d6d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486284"
---
# <a name="determining-workflow-execution-duration-using-tracing"></a>Określanie czasu trwania wykonania przepływu pracy za pomocą śledzenia
W tym temacie pokazano, jak określić czas, jaki zajmuje pomyślnie zakończone, samodzielnie hostowanej przepływu pracy można wykonać przy użyciu śledzenie przepływu pracy.  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a>Aby określić czas wykonywania aplikacji przepływu pracy przy użyciu śledzenie przepływu pracy  
  
1.  Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  Wybierz **pliku**, **nowe**, **projektu**.  W obszarze **C#**, wybierz opcję **przepływu pracy** węzła.  Wybierz **Aplikacja konsoli przepływu pracy** z listy szablonów.  Nazwa nowego projektu `WorkflowDurationTracing` i kliknij przycisk **OK**.  
  
2.  Otwórz Workflow1.xaml.  Przeciągnij <xref:System.Activities.Statements.Delay> działania na powierzchnię projektanta. Właściwości czasu trwania aktywności, należy przypisać wartość 00:00:10 (dziesięć sekund).  
  
3.  Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.  
  
4.  Jeśli nie zostały włączone śledzenie przepływu pracy, rozwiń **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacje serwera aplikacji** . Wybierz **widoku**, **Pokaż analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Włącz dziennik**. Pozostaw otwarte Podgląd zdarzeń, dzięki czemu mogą być wyświetlane dane śledzenia, po uruchomieniu przepływu pracy.  
  
5.  Wykonywanie aplikacji przepływu pracy, naciskając klawisze CTRL + SHIFT + B.  
  
6.  W Podglądzie zdarzeń Znajdź ostatnie zdarzenia przy użyciu Identyfikatora 1009 i komunikat podobny do następującego. Zanotuj czasie rejestrowania komunikatu.  
  
 **Nadrzędne działanie '', DisplayName: '', InstanceId: '' podrzędnych zaplanowanego działania "WorkflowDurationTracking.Workflow1" DisplayName: "Workflow1", Identyfikator InstanceId: "1".**  
  
7.  Znajdź inne ostatnie zdarzenie 1001 identyfikator i komunikat podobny do następującego.  Odejmij poprzedniego czas komunikatu z tego komunikatu zarejestrowane wartości, aby określić czas trwania wykonywania przepływu pracy, która powinna być około 10 sekund.  
  
 **WorkflowInstance Id: "1bbac57b-3322-498e-9e27-8833fda3a5bf" zostało ukończone w stanie zamkniętym.**  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [Windows Server AppFabric monitorowania](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=201275)
