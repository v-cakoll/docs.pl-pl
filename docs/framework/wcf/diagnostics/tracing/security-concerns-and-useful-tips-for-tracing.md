---
title: "Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 07ac814253a563a0cbdad1014970af3d18c6fdde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
W tym temacie opisano, jak możesz chronić poufne informacje z widoczne, a także przydatne porady, korzystając z hostem sieci Web.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Przy użyciu odbiornika śledzenia niestandardowych z hostem sieci Web  
 Podczas pisania własnych nasłuchującego śledzenia, należy zwrócić uwagę możliwość, że śladów mogą zostać utracone w przypadku usługi hostowanej w sieci Web. Podczas odtwarzania WebHost, zamykania procesu na żywo podczas ma duplikat. Jednak dwa procesy muszą mieć dostęp do tego samego zasobu przez pewien czas, który jest zależny od typu odbiornika. W takim przypadku, `XmlWriterTraceListener` tworzy nowy plik śledzenia dla procesu drugi; podczas śledzenia zdarzeń systemu Windows zarządza wiele procesów w tej samej sesji i zapewnia dostęp do tego samego pliku. Jeśli własne odbiornik nie zapewnia funkcje podobne, dane śledzenia mogą zostać utracone, jeśli plik jest zablokowane przez dwa procesy.  
  
 Należy również pamiętać, że odbiornik śledzenia niestandardowych można wysyłać ślady i wiadomości w sieci, na przykład ze zdalną bazą danych. Jako narzędzie wdrażania aplikacji należy skonfigurować niestandardowe odbiorniki z kontroli dostępu. Należy także zastosować kontrolę zabezpieczeń na informacje osobiste, które można uwidocznić w lokalizacjach zdalnych.  
  
## <a name="logging-sensitive-information"></a>Rejestrowanie informacji poufnych  
 Ślady zawierał nagłówków komunikatów, gdy komunikat jest w zakresie. Gdy jest włączone śledzenie, informacje osobiste w nagłówkach specyficzne dla aplikacji, takich jak ciąg zapytania. i body informacje, takie jak numer karty kredytowej, może stać się widoczne w dziennikach. Narzędzia wdrażania aplikacji jest odpowiedzialny za wymuszanie kontroli dostępu do plików konfiguracji i śledzenia. Jeśli nie chcesz, tego rodzaju informacje są widoczne, należy wyłączyć śledzenie lub odfiltrowywania części danych, jeśli chcesz udostępnić dzienniki śledzenia.  
  
 Poniższe porady może pomóc zapobiec przypadkowym ujawnieniem zawartość pliku śledzenia:  
  
-   Upewnij się, że dziennika, które pliki są chronione przez kontroli dostępu zawiera listę (ACL) hosta sieci Web i scenariusze hosta samodzielnego.  
  
-   Wybierz rozszerzenie pliku, który nie może być łatwo przekazywane za pomocą żądania sieci Web. Na przykład rozszerzenie pliku XML nie jest bezpiecznym wyborem. Możesz sprawdzić podręczniku administratora usług IIS umożliwia wyświetlenie listy rozszerzeń, które mogą być przekazywane.  
  
-   Określ ścieżkę bezwzględną do lokalizacji pliku dziennika, która powinna być spoza vroot WebHost publicznego katalogu aby zapobiec uzyskiwany przez innych firm za pomocą przeglądarki sieci Web.  
  
 Domyślnie klucze i dane osobowe lub informacje takie jak nazwa użytkownika i hasło nie jest zalogowany śladów i rejestrowane wiadomości. Administrator maszyny, jednak można użyć `enableLoggingKnownPII` atrybutu w `machineSettings` elementu w pliku Machine.config, aby umożliwić aplikacji uruchomionych na maszynie dziennika znane dane osobowe (dane osobowe) w następujący sposób:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` istnieje element poza pliku Machine.config, system generuje <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Zmiany zaczynają obowiązywać, tylko wtedy, gdy rozpoczyna się lub ponowne uruchomienie aplikacji. Zdarzenie jest rejestrowane podczas uruchamiania, gdy oba atrybuty są ustawione na `true`. Jeśli również zostanie zarejestrowane zdarzenie `logKnownPii` ustawiono `true` , ale `enableLoggingKnownPii` jest `false`.  
  
 Aby uzyskać więcej informacji na rejestrowanie danych osobowych, zobacz [blokada zabezpieczeń PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) próbki.  
  
 Administrator maszyny i wdrażania aplikacji należy zachować wyjątkową ostrożność, korzystając z tych dwóch parametrów. Jeśli włączono rejestrowanie danych osobowych, są rejestrowane kluczy zabezpieczeń i dane osobowe. Jeśli jest wyłączona, dane poufne i specyficzne dla aplikacji jest nadal rejestrowane w nagłówkach wiadomości i treści. Aby uzyskać dokładniejsze omówienie prywatności i ochrony danych osobowych przed przypadkowym, zobacz [zasady zachowania poufności użytkownika](http://go.microsoft.com/fwlink/?LinkID=94647).  
  
 Ponadto adres nadawcy wiadomości jest rejestrowane raz dla każdego połączenia dla transportu z nawiązaniem połączenia i raz na wiadomością wysłaną w przeciwnym razie wartość. Można to zrobić bez zgody nadawcy. Jednak rejestrowanie występuje tylko w informacji lub pełne poziomy śledzenia, które nie są domyślnie lub zalecane poziomy śledzenia w środowisku produkcyjnym, z wyjątkiem live debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
