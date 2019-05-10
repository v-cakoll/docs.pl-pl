---
title: Uwagi dotyczące zabezpieczeń rejestrowania komunikatów
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: e1503249d5fd33e320ccb6642eb6e97c3029ba85
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651827"
---
# <a name="security-concerns-for-message-logging"></a>Uwagi dotyczące zabezpieczeń rejestrowania komunikatów
W tym temacie opisano, jak możesz chronić dane poufne przed przypadkowym w dzienników komunikatów, a także zdarzenia generowane przez rejestrowanie komunikatów.  
  
## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń  
  
### <a name="logging-sensitive-information"></a>Rejestrowanie informacji poufnych  
 Windows Communication Foundation (WCF) nie powoduje modyfikacji wszystkie dane w specyficznych dla aplikacji, nagłówki i treść. Usługi WCF nie śledzi także informacji osobistych w nagłówkach specyficzne dla aplikacji i danych treści.  
  
 Po włączeniu rejestrowania komunikatów, informacje osobiste w nagłówkach specyficzne dla aplikacji, takich jak ciąg zapytania. i body informacje, takie jak numer karty kredytowej, może stać się widoczne w dziennikach. Narzędzia do wdrażania aplikacji jest odpowiedzialny za wymuszania kontroli dostępu do plików dziennika i konfiguracji. Nie należy tego rodzaju informacje są widoczne, należy wyłączyć rejestrowanie lub odfiltrować części danych, jeśli chcesz udostępnić dzienniki.  
  
 Poniższe porady mogą pomóc aby zawartość pliku dziennika przed przypadkowym ujawnieniem:  
  
- Upewnij się, że dziennika, które pliki są chronione przez kontroli dostępu zawiera listę (ACL) zarówno w sieci Web hosta i hosta samodzielnego scenariuszy.  
  
- Wybierz rozszerzenie pliku, który nie może być łatwo przekazywane za pomocą żądania sieci Web. Na przykład rozszerzenie pliku XML nie jest bezpiecznym wyborem. Można sprawdzić w podręczniku administratora usług Internet Information Services (IIS), aby wyświetlić listę rozszerzeń, które mogą być przekazywane.  
  
- Określ ścieżki bezwzględnej do lokalizacji pliku dziennika, która powinna być poza katalogiem publiczny głównego katalogu wirtualnego hosta o sieci Web, aby uniemożliwić dostęp do innych firm za pomocą przeglądarki sieci Web.  
  
 Domyślnie klucze identyfikowalne dane osobowe (PII), takie jak nazwa użytkownika i hasło nie są rejestrowane w śladach i rejestrowane komunikaty. Administrator komputera, jednak można użyć `enableLoggingKnownPII` atrybutu w `machineSettings` elementu w pliku Machine.config, aby zezwolić aplikacji na maszynie się znane identyfikowalne dane osobowe (PII). Następująca konfiguracja pokazuje, jak to zrobić:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Następnie można użyć narzędzia do wdrażania aplikacji `logKnownPii` atrybutu w pliku App.config lub Web.config, aby włączyć dane osobowe rejestrowanie się w następujący sposób:  
  
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
  
 Tylko wtedy, gdy oba ustawienia są `true` jest włączone rejestrowanie danych osobowych. Kombinacja dwóch przełączników umożliwia elastyczne się znane też danych osobowych dla każdej aplikacji.  
  
> [!IMPORTANT]
>  W [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` i `logKnownPii` również musi mieć wartość flagi `true` w pliku Web.config lub w pliku App.config, aby włączyć rejestrowanie dane osobowe, tak jak pokazano w poniższym przykładzie `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Należy pamiętać, jeśli określisz co najmniej dwóch źródeł niestandardowych w pliku konfiguracji, tylko atrybuty pierwszego źródła są odczytywane. Pozostałe są ignorowane. Oznacza to, że dla następujących App.config, plik, dane osobowe nie jest rejestrowana dla obu źródeł, mimo, że rejestrowanie danych osobowych jest jawnie włączone dla drugiego źródła.  
  
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
  
 Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` element istnieje poza pliku Machine.config, system generuje <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Zmiany zostaną zastosowane, tylko wtedy, gdy rozpoczyna się lub ponowne uruchomienie aplikacji. Zdarzenie jest rejestrowane podczas uruchamiania, gdy oba atrybuty są ustawione na `true`. Jeśli zdarzenie jest również rejestrowana `logKnownPii` ustawiono `true` , ale `enableLoggingKnownPii` jest `false`.  
  
 Administrator maszyny i wdrażania aplikacji należy zachować wyjątkową ostrożność, korzystając z tych dwóch przełączników. Jeśli włączono rejestrowanie dane osobowe, kluczy zabezpieczeń i dane osobowe są rejestrowane. Jeśli jest wyłączone, dane poufne i specyficzne dla aplikacji są nadal rejestrowane w wiadomości nagłówki i treść. Aby uzyskać bardziej szczegółowe omówienie ochrony prywatności i ochrony danych osobowych przed przypadkowym zobacz [rozwiązania prywatność użytkownika](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  Dane osobowe nie jest ukryty w źle sformułowane komunikaty. Takie messaged są rejestrowane jako — bez żadnych modyfikacji. Atrybuty wymienione wcześniej nie mają wpływu na to.  
  
### <a name="custom-trace-listener"></a>Odbiornik śledzenia niestandardowe  
 Dodawanie odbiornika śledzenia niestandardowe dotyczące rejestrowania komunikatu źródła śledzenia jest uprawnień, które powinny być ograniczone do administratora. Jest to spowodowane złośliwego niestandardowe odbiorniki można skonfigurować do wysyłania wiadomości zdalnie, co prowadzi do ujawnienia poufnych informacji. Ponadto jeśli skonfigurujesz niestandardowe odbiornika do wysyłania wiadomości na łączu, takich jak ze zdalną bazą danych powinien wymuszać kontrolę dostępu dla dzienników komunikatów na komputerze zdalnym.  
  
## <a name="events-triggered-by-message-logging"></a>Zdarzenia wyzwolone przez rejestrowanie komunikatów  
 Poniższa lista zawiera wszystkie zdarzenia, które są emitowane przez rejestrowanie komunikatów.  
  
- Komunikat o błędzie logowania: To zdarzenie jest emitowane, gdy rejestrowanie komunikatów jest włączona w konfiguracji lub za pomocą usługi WMI. Zawartość zdarzenia jest "włączone rejestrowanie komunikatów. Informacje poufne może zostać zarejestrowane w postaci zwykłego tekstu, nawet jeśli zostały zaszyfrowane w sieci, na przykład, treści wiadomości."  
  
- Trwa wylogowywanie komunikat: To zdarzenie jest emitowane, jeśli rejestrowanie komunikatów jest wyłączone za pomocą usługi WMI. Zawartość zdarzenia jest "Komunikat rejestrowanie zostało wyłączone."  
  
- Znany też danych osobowych Zaloguj się: To zdarzenie jest emitowane, gdy jest włączone rejestrowanie znane też danych osobowych. Dzieje się tak po `enableLoggingKnownPii` atrybutu w `machineSettings` element w pliku Machine.config jest ustawiony na `true`i `logKnownPii` atrybutu `source` element w pliku App.config lub Web.config jest ustawiony na `true`.  
  
- Zaloguj się znane też danych osobowych, które są niedozwolone: To zdarzenie jest emitowane podczas rejestrowania znane dane osobowe nie jest dozwolone. Dzieje się tak po `logKnownPii` atrybutu `source` element w pliku App.config lub Web.config jest ustawiony na `true`, ale `enableLoggingKnownPii` atrybutu w `machineSettings` element w pliku Machine.config jest ustawiony na `false`. Jest zgłaszany żaden wyjątek.  
  
 Zdarzenia te można wyświetlać w narzędziu Podgląd zdarzeń, które pochodzą z Windows. Aby uzyskać więcej informacji na temat tego, zobacz [rejestrowania zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Zobacz także

- [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
