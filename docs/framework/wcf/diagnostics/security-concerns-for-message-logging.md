---
title: Uwagi dotyczące zabezpieczeń rejestrowania komunikatów
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: b635591b7a3b07385ed48c6b1ea556139c6d77c5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044254"
---
# <a name="security-concerns-for-message-logging"></a>Uwagi dotyczące zabezpieczeń rejestrowania komunikatów
W tym temacie opisano, jak można chronić poufne dane przed ujawnieniem w dziennikach komunikatów, a także zdarzenia generowane przez funkcję rejestrowania komunikatów.  
  
## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń  
  
### <a name="logging-sensitive-information"></a>Rejestrowanie poufnych informacji  
 Windows Communication Foundation (WCF) nie modyfikuje żadnych danych w nagłówkach i treści specyficznych dla aplikacji. Funkcja WCF nie śledzi również informacji osobistych w nagłówkach lub danych treści specyficznych dla aplikacji.  
  
 Po włączeniu rejestrowania komunikatów informacje osobiste w nagłówkach specyficznych dla aplikacji, takie jak ciąg zapytania; i informacje o treści, takie jak numer karty kredytowej, mogą stać się widoczne w dziennikach. Narzędzie wdrażania aplikacji jest odpowiedzialne za wymuszanie kontroli dostępu do plików konfiguracyjnych i dzienników. Jeśli nie chcesz, aby ten rodzaj informacji był widoczny, należy wyłączyć rejestrowanie lub przefiltrować część danych, jeśli chcesz udostępnić dzienniki.  
  
 Poniższe porady mogą pomóc zapobiec przypadkowemu ujawnieniu zawartości pliku dziennika:  
  
- Upewnij się, że pliki dziennika są chronione za pomocą list Access Control (ACL) zarówno w scenariuszach hosta sieci Web, jak i z dowolnego hosta.  
  
- Wybierz rozszerzenie pliku, którego nie można łatwo obsłużyć przy użyciu żądania sieci Web. Na przykład rozszerzenie pliku XML nie jest bezpiecznym wyborem. Aby wyświetlić listę rozszerzeń, które mogą być obsługiwane, można sprawdzić Przewodnik administrowania Internet Information Services (IIS).  
  
- Określ ścieżkę bezwzględną dla lokalizacji pliku dziennika, która powinna znajdować się poza katalogiem publicznym wirtualnego katalogu głównego hosta sieci Web, aby uniemożliwić dostęp do niej przez stronę zewnętrzną przy użyciu przeglądarki sieci Web.  
  
 Domyślnie klucze i dane osobowe, takie jak nazwa użytkownika i hasło, nie są rejestrowane w śladach i zarejestrowanych komunikatach. Administrator komputera może jednak użyć `enableLoggingKnownPII` atrybutu `machineSettings` w pliku Machine. config, aby zezwolić aplikacjom działającym na maszynie na rejestrowanie znanych informacji osobistych. W poniższej konfiguracji pokazano, jak to zrobić:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Narzędzie do wdrażania aplikacji może następnie użyć `logKnownPii` atrybutu w pliku App. config lub Web. config, aby umożliwić logowanie do Internetu w następujący sposób:  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
    </sources>  
</system.diagnostics>  
```  
  
 Tylko wtedy, gdy oba `true` ustawienia są włączone do rejestrowania przez dane osobowe. Kombinacja dwóch przełączników pozwala elastycznie rejestrować znane dane OSOBowe dla każdej aplikacji.  
  
> [!IMPORTANT]
> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `true` We flagach `logKnownPii` `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`i należy również ustawić w pliku Web. config lub pliku App. config, aby umożliwić rejestrowanie danych osobowych, jak pokazano w poniższym przykładzie. `logEntireMessage`  
  
 Należy pamiętać, że w przypadku określenia co najmniej dwóch źródeł niestandardowych w pliku konfiguracyjnym odczytywane są tylko atrybuty pierwszego źródła. Pozostałe są ignorowane. Oznacza to, że w przypadku następującego pliku App. config plik, dane OSOBowe nie są rejestrowane dla obu źródeł, nawet gdy rejestrowanie danych osobowych jest jawnie włączone dla drugiego źródła.  
  
```xml  
<system.diagnostics>  
   <sources>  
      <source name="System.ServiceModel.MessageLogging"  
              logKnownPii="false">  
              <listeners>  
                 <add name="messages"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\messages.svclog" />  
              </listeners>  
            </source>  
      <source name="System.ServiceModel"   
              logKnownPii="true">  
              <listeners>  
                 <add name="traces"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\traces.svclog" />  
              </listeners>  
      </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Jeśli element istnieje poza plikiem Machine. config, system <xref:System.Configuration.ConfigurationErrorsException>zgłasza. `<machineSettings enableLoggingKnownPii="Boolean"/>`  
  
 Zmiany są skuteczne tylko wtedy, gdy aplikacja jest uruchamiana lub uruchamiana ponownie. Zdarzenie jest rejestrowane przy uruchamianiu, gdy oba atrybuty są ustawione `true`na. Zdarzenie jest rejestrowane również wtedy, `logKnownPii` gdy jest ustawione `true` na `enableLoggingKnownPii` , `false`ale jest.  
  
 W przypadku korzystania z tych dwóch przełączników administrator komputera i narzędzie wdrażania aplikacji powinny mieć wyjątkową ostrożność. W przypadku włączenia rejestrowania przez dane OSOBowe są rejestrowane klucze zabezpieczeń i dane OSOBowe. Jeśli jest wyłączona, poufne i specyficzne dla aplikacji dane są nadal rejestrowane w nagłówkach i treściach komunikatów. Bardziej szczegółowe omówienie ochrony prywatności i ochrony danych osobowych przed ujawnieniem można znaleźć w temacie [prywatność użytkowników](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
> Dane OSOBowe nie są ukryte w źle sformułowanych wiadomościach. Takie komunikaty są rejestrowane bez żadnych modyfikacji. Opisane wcześniej atrybuty nie mają wpływu na to.  
  
### <a name="custom-trace-listener"></a>Odbiornik śledzenia niestandardowego  
 Dodawanie niestandardowego odbiornika śledzenia do źródła śledzenia rejestrowania komunikatów jest uprawnieniem, które powinno być ograniczone do administratora. Jest to spowodowane tym, że złośliwe niestandardowe odbiorniki można skonfigurować do zdalnego wysyłania wiadomości, co prowadzi do ujawnienia poufnych informacji. Ponadto, jeśli skonfigurujesz odbiornik niestandardowy do wysyłania komunikatów do sieci, takich jak, do zdalnej bazy danych, należy wymusić odpowiednią kontrolę dostępu do dzienników komunikatów na komputerze zdalnym.  
  
## <a name="events-triggered-by-message-logging"></a>Zdarzenia wyzwalane przez rejestrowanie komunikatów  
 Poniżej wymieniono wszystkie zdarzenia emitowane przez funkcję rejestrowania komunikatów.  
  
- Rejestrowanie komunikatów: To zdarzenie jest emitowane, gdy rejestrowanie komunikatów jest włączone w konfiguracji lub za pomocą usługi WMI. Zawartość zdarzenia to "rejestrowanie komunikatów zostało włączone. Poufne informacje mogą być rejestrowane w postaci zwykłego tekstu, nawet jeśli zostały zaszyfrowane w sieci, na przykład treści wiadomości ".  
  
- Wylogowanie komunikatu: To zdarzenie jest emitowane, gdy rejestrowanie komunikatów jest wyłączone za pomocą usługi WMI. Zawartość zdarzenia to "rejestrowanie komunikatów zostało wyłączone".  
  
- Rejestruj znane dane OSOBowe na: To zdarzenie jest emitowane, gdy jest włączone rejestrowanie znanego elementu dane OSOBowe. Dzieje się tak, `enableLoggingKnownPii` gdy atrybut `machineSettings` w elemencie pliku Machine. config jest `logKnownPii` ustawiony na `true`, a atrybut `source` elementu w pliku App. config lub Web. config jest ustawiony na `true`.  
  
- Znane dane OSOBowe nie są dozwolone w dzienniku: To zdarzenie jest emitowane, gdy rejestrowanie znanego elementu dane OSOBowe jest niedozwolone. Dzieje się tak, `logKnownPii` gdy atrybut `source` elementu w pliku App. config lub Web. config jest `enableLoggingKnownPii` ustawiony na `true`, ale atrybut w `machineSettings` elemencie Machine. config jest ustawiony na `false`. Nie zgłoszono żadnego wyjątku.  
  
 Te zdarzenia można wyświetlać w narzędziu Podgląd zdarzeń, które są dostarczane z systemem Windows. Aby uzyskać więcej informacji na ten temat, zobacz [Rejestrowanie zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
