---
title: Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 5ced4f3a3a5e83564703db88b28ee2b3c6eeb1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185721"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
W tym temacie opisano, jak można chronić poufne informacje przed narażoną, a także przydatne wskazówki podczas korzystania z webhost.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Korzystanie z niestandardowego odbiornika śledzenia za pomocą usługi WebHost  
 Jeśli piszesz własny odbiornik śledzenia, należy pamiętać o możliwości, że ślady mogą zostać utracone w przypadku usługi hostowane w sieci Web. Gdy WebHost odtwarza, zamyka proces na żywo, podczas gdy duplikat przejmuje. Jednak dwa procesy muszą nadal mieć dostęp do tego samego zasobu przez pewien czas, który jest zależny od typu odbiornika. W takim przypadku `XmlWriterTraceListener` , tworzy nowy plik śledzenia dla drugiego procesu; podczas śledzenia zdarzeń systemu Windows zarządza wieloma procesami w ramach tej samej sesji i daje dostęp do tego samego pliku. Jeśli własny odbiornik nie zapewnia podobnych funkcji, ślady mogą zostać utracone, gdy plik jest zablokowany przez dwa procesy.  
  
 Należy również pamiętać, że niestandardowy odbiornik śledzenia może wysyłać ślady i wiadomości w sieci, na przykład do zdalnej bazy danych. Jako wdrażający aplikację należy skonfigurować niestandardowe odbiorniki z odpowiednią kontrolą dostępu. Należy również zastosować kontrolę zabezpieczeń w odniesieniu do wszelkich informacji osobistych, które mogą być ujawnione w lokalizacji zdalnej.  
  
## <a name="logging-sensitive-information"></a>Rejestrowanie poufnych informacji  
 Ślady zawierają nagłówki wiadomości, gdy wiadomość jest w zakresie. Gdy śledzenie jest włączone, informacje osobiste w nagłówkach specyficznych dla aplikacji, takich jak ciąg zapytania; informacje o treści, takie jak numer karty kredytowej, mogą stać się widoczne w dziennikach. Wdrażający aplikację jest odpowiedzialny za wymuszanie kontroli dostępu w plikach konfiguracji i śledzenia. Jeśli nie chcesz, aby tego rodzaju informacje były widoczne, należy wyłączyć śledzenie lub odfiltrować część danych, jeśli chcesz udostępnić dzienniki śledzenia.  
  
 Poniższe wskazówki mogą pomóc w zapobieganiu niezamierzonej instynkowaniu zawartości pliku śledzenia:  
  
- Upewnij się, że pliki dziennika są chronione przez listy kontroli dostępu (ACL) zarówno w webhost i scenariuszy hosta własnego.  
  
- Wybierz rozszerzenie pliku, które nie może być łatwo obsługiwane za pomocą żądania sieci Web. Na przykład rozszerzenie pliku xml nie jest bezpiecznym wyborem. Można zapoznać się z przewodnikiem administracyjnym iis, aby wyświetlić listę rozszerzeń, które mogą być obsługiwane.  
  
- Określ ścieżkę bezwzględną dla lokalizacji pliku dziennika, która powinna znajdować się poza katalogiem publicznym WebHost vroot, aby uniemożliwić dostęp do niej przez stronę zewnętrzną za pomocą przeglądarki sieci Web.  
  
 Domyślnie klucze i informacje umożliwiające identyfikację użytkownika, takie jak nazwa użytkownika i hasło, nie są rejestrowane w ślady i rejestrowane wiadomości. Administrator komputera może jednak użyć `enableLoggingKnownPII` atrybutu `machineSettings` w elemencie pliku Machine.config, aby umożliwić aplikacjom uruchomionym na komputerze rejestrowanie znanych informacji umożliwiających identyfikację użytkownika w następujący sposób:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` element istnieje poza plikiem Machine.config, system <xref:System.Configuration.ConfigurationErrorsException>zgłasza plik .  
  
 Zmiany są skuteczne tylko wtedy, gdy aplikacja zostanie uruchomiona lub ponownie uruchomiona. Zdarzenie jest rejestrowane podczas uruchamiania, gdy `true`oba atrybuty są ustawione na . Zdarzenie jest również rejestrowane, `logKnownPii` jeśli `true` `enableLoggingKnownPii` jest `false`ustawione, ale jest .  
  
 Aby uzyskać więcej informacji na temat rejestrowania informacji umożliwiających identyfikację, zobacz przykład [blokady zabezpieczeń pii.](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md)  
  
 Administrator komputera i wdrażający aplikacje powinni zachować szczególną ostrożność podczas korzystania z tych dwóch przełączników. Jeśli rejestrowanie danych umożliwiających identyfikację jest włączone, rejestrowane są klucze zabezpieczeń i dane umożliwiające identyfikację. Jeśli jest wyłączona, poufne i specyficzne dla aplikacji dane są nadal rejestrowane w nagłówkach wiadomości i treści. Aby uzyskać dokładniejszą dyskusję na temat prywatności i ochrony informacji umożliwiających identyfikację użytkownika przed narażeniem, zobacz [Prywatność użytkowników](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
 Ponadto adres IP nadawcy wiadomości jest rejestrowany raz na połączenie dla transportów zorientowanych na połączenie, a raz na wiadomość wysłaną w inny sposób. Odbywa się to bez zgody nadawcy. Jednak to rejestrowanie występuje tylko na poziomach śledzenia informacji lub pełnej, które nie są domyślnymi lub zalecanymi poziomami śledzenia w produkcji, z wyjątkiem debugowania na żywo.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
