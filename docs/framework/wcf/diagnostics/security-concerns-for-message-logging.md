---
title: Uwagi dotyczące zabezpieczeń rejestrowania komunikatów
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: bb1a6ab84ceba27b398d397b4407a55aa02c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185774"
---
# <a name="security-concerns-for-message-logging"></a>Uwagi dotyczące zabezpieczeń rejestrowania komunikatów
W tym temacie opisano, jak można chronić poufne dane przed udostępnianiem w dziennikach komunikatów, a także zdarzenia generowane przez rejestrowanie wiadomości.  
  
## <a name="security-concerns"></a>Kwestie bezpieczeństwa  
  
### <a name="logging-sensitive-information"></a>Rejestrowanie poufnych informacji  
 Windows Communication Foundation (WCF) nie modyfikuje żadnych danych w nagłówkach i treści specyficzne dla aplikacji. WCF również nie śledzi informacji osobistych w nagłówkach specyficznych dla aplikacji lub danych treści.  
  
 Gdy rejestrowanie wiadomości jest włączone, informacje osobiste w nagłówkach specyficznych dla aplikacji, takie jak ciąg zapytania; informacje o treści, takie jak numer karty kredytowej, mogą stać się widoczne w dziennikach. Wdrażający aplikację jest odpowiedzialny za wymuszanie kontroli dostępu w plikach konfiguracji i dziennika. Jeśli nie chcesz, aby tego rodzaju informacje były widoczne, należy wyłączyć rejestrowanie lub odfiltrować część danych, jeśli chcesz udostępnić dzienniki.  
  
 Poniższe wskazówki mogą pomóc w zapobieganiu niezamierzonej insytowaniu zawartości pliku dziennika:  
  
- Upewnij się, że pliki dziennika są chronione przez listy kontroli dostępu (ACL) zarówno w scenariuszach hosta sieci Web, jak i hosta samodzielnego.  
  
- Wybierz rozszerzenie pliku, które nie może być łatwo obsługiwane za pomocą żądania sieci Web. Na przykład rozszerzenie pliku xml nie jest bezpiecznym wyborem. Listę rozszerzeń, które mogą być przekazywane, można znaleźć w podręczniku administratora usług Internet Information Services (IIS).  
  
- Określ ścieżkę bezwzględną dla lokalizacji pliku dziennika, która powinna znajdować się poza katalogiem publicznym vroot hosta sieci Web, aby uniemożliwić dostęp do niego przez stronę zewnętrzną za pomocą przeglądarki sieci Web.  
  
 Domyślnie klucze i informacje umożliwiające identyfikację użytkownika, takie jak nazwa użytkownika i hasło, nie są rejestrowane w ślady i rejestrowane wiadomości. Administrator komputera może jednak użyć `enableLoggingKnownPII` atrybutu `machineSettings` w elemencie pliku Machine.config, aby zezwolić aplikacjom działającym na komputerze na rejestrowanie znanych informacji umożliwiających identyfikację użytkownika. Następująca konfiguracja pokazuje, jak to zrobić:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>
```  
  
 Wdrażający aplikację może następnie `logKnownPii` użyć atrybutu w pliku App.config lub Web.config, aby włączyć rejestrowanie danych umożliwiających identyfikację użytkowników w następujący sposób:  
  
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
  
 Tylko wtedy, `true` gdy oba ustawienia są włączone rejestrowanie pii. Połączenie dwóch przełączników umożliwia elastyczność rejestrowania znanych identyfikatorów umożliwiających identyfikację dla każdej aplikacji.  
  
> [!IMPORTANT]
> W [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` i `logKnownPii` flagi muszą być `true` również ustawione w pliku Web.config lub app.config pliku, aby włączyć `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`rejestrowanie pii, jak pokazano w poniższym przykładzie .  
  
 Należy pamiętać, że jeśli określisz dwa lub więcej źródeł niestandardowych w pliku konfiguracyjnym, odczytywane są tylko atrybuty pierwszego źródła. Pozostałe są ignorowane. Oznacza to, że dla następującego pliku App.config, informacje umożliwiające identyfikację nie są rejestrowane dla obu źródeł, mimo że rejestrowanie danych umożliwiających identyfikację jest jawnie włączone dla drugiego źródła.  
  
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
  
 Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` element istnieje poza plikiem Machine.config, system <xref:System.Configuration.ConfigurationErrorsException>zgłasza plik .  
  
 Zmiany są skuteczne tylko wtedy, gdy aplikacja zostanie uruchomiona lub ponownie uruchomiona. Zdarzenie jest rejestrowane podczas uruchamiania, gdy `true`oba atrybuty są ustawione na . Zdarzenie jest również rejestrowane, `logKnownPii` jeśli `true` `enableLoggingKnownPii` jest `false`ustawione, ale jest .  
  
 Administrator komputera i wdrażający aplikacje powinni zachować szczególną ostrożność podczas korzystania z tych dwóch przełączników. Jeśli rejestrowanie danych umożliwiających identyfikację jest włączone, rejestrowane są klucze zabezpieczeń i dane umożliwiające identyfikację. Jeśli jest wyłączona, poufne i specyficzne dla aplikacji dane są nadal rejestrowane w nagłówkach wiadomości i treści. Aby uzyskać dokładniejszą dyskusję na temat prywatności i ochrony informacji umożliwiających identyfikację użytkownika przed narażeniem, zobacz [Prywatność użytkowników](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
> [!CAUTION]
> Informacje umożliwiające identyfikację nie są ukryte w nieprawidłowo sformułowanych wiadomościach. Takie messaged są rejestrowane jako -jest bez żadnych modyfikacji. Atrybuty wymienione wcześniej nie mają wpływu na to.  
  
### <a name="custom-trace-listener"></a>Niestandardowy odbiornik śledzenia  
 Dodawanie niestandardowego odbiornika śledzenia w źródle śledzenia rejestrowania wiadomości jest uprawnieniem, które powinno być ograniczone do administratora. Dzieje się tak, ponieważ złośliwe detektory niestandardowe mogą być skonfigurowane do wysyłania wiadomości zdalnie, co prowadzi do ujawnienia poufnych informacji. Ponadto jeśli skonfigurować odbiornika niestandardowego do wysyłania wiadomości w sieci, takich jak, do zdalnej bazy danych, należy wymusić właściwą kontrolę dostępu na dziennikach komunikatów na komputerze zdalnym.  
  
## <a name="events-triggered-by-message-logging"></a>Zdarzenia wyzwalane przez rejestrowanie wiadomości  
 Poniżej wymieniono wszystkie zdarzenia emitowane przez rejestrowanie wiadomości.  
  
- Rejestrowanie wiadomości: to zdarzenie jest emitowane, gdy rejestrowanie wiadomości jest włączone w konfiguracji lub za pośrednictwem usługi WMI. Zawartość zdarzenia jest "Rejestrowanie wiadomości zostało włączone. Poufne informacje mogą być rejestrowane w postaci zwykłego tekstu, nawet jeśli były szyfrowane w sieci, na przykład w treściach wiadomości."  
  
- Wylogowywanie się wiadomości: to zdarzenie jest emitowane, gdy rejestrowanie wiadomości jest wyłączone za pośrednictwem usługi WMI. Zawartość zdarzenia jest "Rejestrowanie wiadomości zostało wyłączone."  
  
- Zaloguj znane informacje umożliwiające identyfikację: to zdarzenie jest emitowane po włączeniu rejestrowania znanych danych umożliwiających identyfikację. Dzieje się `enableLoggingKnownPii` tak, gdy `machineSettings` atrybut w elemencie pliku `true`Machine.config jest ustawiony na , a `logKnownPii` atrybut `source` elementu w pliku App.config lub Web.config jest ustawiony na `true`.  
  
- Log Znane informacje umożliwiające identyfikację: To zdarzenie jest emitowane, gdy rejestrowanie znanych identyfikatorów umożliwiających identyfikację jest niedozwolone. Dzieje się `logKnownPii` tak, gdy `source` atrybut elementu w pliku App.config lub Web.config `true` `enableLoggingKnownPii` jest ustawiony `machineSettings` na , ale atrybut w elemencie pliku Machine.config jest ustawiony na `false`. Wyjątek nie jest zgłaszany.  
  
 Zdarzenia te można wyświetlać w narzędziu Podgląd zdarzeń dostarczanym z systemem Windows. Aby uzyskać więcej informacji na ten temat, zobacz [Rejestrowanie zdarzeń](./event-logging/index.md).  
  
## <a name="see-also"></a>Zobacz też

- [Rejestrowanie komunikatów](message-logging.md)
- [Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia](./tracing/security-concerns-and-useful-tips-for-tracing.md)
