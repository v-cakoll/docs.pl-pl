---
title: Uwagi dotyczące zabezpieczeń rejestrowania komunikatów
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0ca5eee4d4a1fd0dfaabbf9160488eb2d88f3d3d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804134"
---
# <a name="security-concerns-for-message-logging"></a>Uwagi dotyczące zabezpieczeń rejestrowania komunikatów
W tym temacie opisano, jak możesz chronić poufne dane z ujawniany w dzienników komunikatów, a także zdarzenia generowane przez rejestrowanie komunikatów.  
  
## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń  
  
### <a name="logging-sensitive-information"></a>Rejestrowanie informacji poufnych  
 Windows Communication Foundation (WCF) nie modyfikuje danych w nagłówkach specyficzne dla aplikacji i treść. Usługi WCF nie śledzi również informacje osobiste w nagłówkach specyficzne dla aplikacji i danych treści.  
  
 Po włączeniu rejestrowania komunikatów, informacje osobiste w nagłówkach specyficzne dla aplikacji, takich jak ciąg zapytania. i body informacje, takie jak numer karty kredytowej, może stać się widoczne w dziennikach. Narzędzia wdrażania aplikacji jest odpowiedzialny za egzekwowanie kontrolę dostępu dla plików dziennika i konfiguracji. Jeśli nie chcesz, tego rodzaju informacje są widoczne, należy wyłączyć rejestrowanie lub odfiltrować części danych, jeśli chcesz udostępnić dzienniki.  
  
 Poniższe porady mogą ułatwić zapobiec przypadkowym ujawnieniem treści pliku dziennika:  
  
-   Upewnij się, że dziennika, które pliki są chronione przez kontroli dostępu zawiera listę (ACL) hosta sieci Web i hosta samodzielnego scenariuszy.  
  
-   Wybierz rozszerzenie pliku, który nie może być łatwo przekazywane za pomocą żądania sieci Web. Na przykład rozszerzenie pliku XML nie jest bezpiecznym wyborem. Możesz sprawdzić Przewodnik administrowania Internet Information Services (IIS), aby wyświetlić listę rozszerzeń, które mogą być przekazywane.  
  
-   Określ ścieżkę bezwzględną do lokalizacji pliku dziennika, które powinny być poza katalog sieci Web hosta vroot publicznego aby zapobiec uzyskiwany przez innych firm za pomocą przeglądarki sieci Web.  
  
 Domyślnie klucze i dane osobowe lub informacje takie jak nazwa użytkownika i hasło nie jest zalogowany śladów i rejestrowane wiadomości. Administrator maszyny, jednak można użyć `enableLoggingKnownPII` atrybutu w `machineSettings` elementu w pliku Machine.config, aby umożliwić aplikacji uruchomionych na maszynie znane dane osobowe lub informacje logowania. Następująca konfiguracja pokazano, jak to zrobić:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Następnie można użyć narzędzia wdrażania aplikacji `logKnownPii` atrybutu w pliku App.config lub Web.config, aby włączyć dane osobowe rejestrowania w następujący sposób:  
  
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
  
 Tylko wtedy, gdy oba ustawienia są `true` jest włączone rejestrowanie danych osobowych. Kombinacja dwa przełączniki zapewnia elastyczność do logowania znane dane osobowe dla każdej aplikacji.  
  
> [!IMPORTANT]
>  W [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` i `logKnownPii` flagi należy również wybrać opcję `true` w pliku Web.config lub w pliku App.config, aby włączyć rejestrowanie danych osobowych, Pokaż tak jak w poniższym przykładzie `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Należy zwrócić uwagę, jeśli określisz dwóch lub więcej źródeł niestandardowych w pliku konfiguracji, tylko atrybuty pierwszego źródła są odczytywane. Pozostałe są ignorowane. Oznacza to, że dla następującego pliku App.config, plik, dane osobowe nie jest zalogowany dla obu źródeł, mimo że jawnie włączono rejestrowanie danych osobowych drugie źródło.  
  
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
  
 Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` istnieje element poza pliku Machine.config, system generuje <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Zmiany zaczynają obowiązywać, tylko wtedy, gdy rozpoczyna się lub ponowne uruchomienie aplikacji. Zdarzenie jest rejestrowane podczas uruchamiania, gdy oba atrybuty są ustawione na `true`. Jeśli również zostanie zarejestrowane zdarzenie `logKnownPii` ustawiono `true` , ale `enableLoggingKnownPii` jest `false`.  
  
 Administrator maszyny i wdrażania aplikacji należy zachować wyjątkową ostrożność, korzystając z tych dwóch parametrów. Jeśli włączono rejestrowanie danych osobowych, są rejestrowane kluczy zabezpieczeń i dane osobowe. Jeśli jest wyłączona, dane poufne i specyficzne dla aplikacji jest nadal rejestrowane w nagłówkach wiadomości i treści. Aby uzyskać bardziej szczegółowe omówienie prywatności i ochrony danych osobowych przed przypadkowym zobacz [zasady zachowania poufności użytkownika](http://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  Dane osobowe nie jest ukryty w wadliwe komunikaty. Takie messaged są rejestrowane jako — bez żadnych modyfikacji. Atrybuty wymienione wcześniej nie mają wpływu na tym.  
  
### <a name="custom-trace-listener"></a>Odbiornik śledzenia niestandardowych  
 Dodawanie odbiornika śledzenia niestandardowych na rejestrowania komunikatów źródła śledzenia jest uprawnień, które powinny być ograniczone do administratora. Wynika to z faktu złośliwego niestandardowe odbiorniki można skonfigurować do wysyłania wiadomości zdalnie, która prowadzi do ujawnienie poufnych informacji. Ponadto możesz skonfigurować niestandardowe odbiornika do wysyłania wiadomości w sieci, takich jak ze zdalną bazą danych, powinien wymuszać kontrolę dostępu do dzienników komunikatów w komputerze zdalnym.  
  
## <a name="events-triggered-by-message-logging"></a>Zdarzenia wyzwolone przez rejestrowanie komunikatów  
 Poniższa lista zawiera wszystkie zdarzenia, które są emitowane przez rejestrowanie komunikatów.  
  
-   Komunikat logowania: to zdarzenie jest emitowany po włączeniu rejestrowania komunikatów w konfiguracji lub za pomocą usługi WMI. Zawartość zdarzenia jest "włączono rejestrowanie komunikatów. Poufne informacje mogą być rejestrowane w postaci zwykłego tekstu, nawet jeśli zostały one zaszyfrowane w trakcie przesyłania, na przykład treści wiadomości."  
  
-   Komunikat wylogowanie: to zdarzenie jest emitowany wyłączenie rejestrowania komunikatów za pomocą usługi WMI. Zawartość zdarzenia jest "Komunikat rejestrowanie zostało wyłączone."  
  
-   Dziennik znane dane osobowe na: To zdarzenie jest emitowany, gdy jest włączone rejestrowanie znanych danych osobowych. Dzieje się tak podczas `enableLoggingKnownPii` atrybutu w `machineSettings` element w pliku Machine.config jest ustawiony na wartość `true`i `logKnownPii` atrybutu `source` element w pliku App.config lub Web.config jest ustawiony na wartość `true`.  
  
-   Zaloguj się znane dane osobowe niedozwolone: to zdarzenie jest emitowany, gdy rejestrowanie znanych danych nie jest dozwolone. Dzieje się tak podczas `logKnownPii` atrybutu `source` element w pliku App.config lub Web.config jest ustawiony na wartość `true`, ale `enableLoggingKnownPii` atrybutu w `machineSettings` element w pliku Machine.config jest ustawiony na wartość `false`. Nie wyjątek.  
  
 Zdarzenia te można wyświetlać w narzędziu Podgląd zdarzeń, z dołączoną do systemu Windows. Aby uzyskać więcej informacji o tym, zobacz [rejestrowania zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
