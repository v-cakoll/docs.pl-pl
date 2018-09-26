---
title: Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
author: BrucePerlerMS
ms.openlocfilehash: 51db352913999d5527ead5273e6488cd09d88670
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207802"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
W tym temacie opisano, jak możesz chronić poufne informacje przed przypadkowym, a także przydatne porady, korzystając z hostem sieci Web.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Używanie odbiornika śledzenia niestandardowe z hostem sieci Web  
 Jeśli piszesz detektor śledzenia, należy pamiętać o możliwości śledzenia może zniknąć w przypadku usługi hostowanej w sieci Web. Podczas odtwarzania hostem sieci Web, wyłącza żywy proces podczas duplikatu przejmuje. Jednak dwa procesy muszą mieć dostęp do tego samego zasobu przez pewien czas, który jest zależny od typu odbiornika. W tym przypadku, `XmlWriterTraceListener` tworzy nowy plik śledzenia dla drugiego procesu; podczas gdy zarządza wiele procesów w ramach tej samej sesji śledzenia zdarzeń Windows i zapewnia dostęp do tego samego pliku. Jeśli odbiornik własne nie zapewnia podobne funkcje, ślady mogą zostać utracone, jeśli plik jest zablokowany w przy użyciu dwóch procesów.  
  
 Należy również pamiętać, że odbiornik śledzenia niestandardowe można wysłać ślady i komunikatów w sieci, na przykład ze zdalną bazą danych. Narzędzia do wdrażania aplikacji należy skonfigurować niestandardowe odbiorniki przy użyciu kontroli dostępu. Należy również zastosować kontroli zabezpieczeń na informacje osobiste, może być udostępniona w lokalizacjach zdalnych.  
  
## <a name="logging-sensitive-information"></a>Rejestrowanie informacji poufnych  
 Ślady zawierają nagłówki wiadomości, gdy komunikat jest w zakresie. Jeśli śledzenie jest włączone, informacje osobiste w nagłówkach specyficzne dla aplikacji, takich jak ciąg zapytania. i body informacje, takie jak numer karty kredytowej, może stać się widoczne w dziennikach. Narzędzia do wdrażania aplikacji jest odpowiedzialny za wymuszania kontroli dostępu do plików konfiguracji i śledzenia. Nie należy tego rodzaju informacje są widoczne, należy wyłączyć śledzenie lub odfiltrować części danych, jeśli chcesz udostępnić dzienniki śledzenia.  
  
 Poniższe porady mogą pomóc aby zawartość pliku śledzenia przed przypadkowym ujawnieniem:  
  
-   Upewnij się, że dziennika, które pliki są chronione przez kontroli dostępu zawiera listę (ACL) zarówno w hosta samodzielnego scenariuszy i hostem sieci Web.  
  
-   Wybierz rozszerzenie pliku, który nie może być łatwo przekazywane za pomocą żądania sieci Web. Na przykład rozszerzenie pliku XML nie jest bezpiecznym wyborem. Można sprawdzić w podręczniku administratora usług IIS, aby wyświetlić listę rozszerzeń, które mogą być przekazywane.  
  
-   Określ ścieżki bezwzględnej do lokalizacji pliku dziennika, która powinna być poza katalogiem WebHost publiczny głównego katalogu wirtualnego, aby uniemożliwić dostęp do innych firm za pomocą przeglądarki sieci Web.  
  
 Domyślnie klucze identyfikowalne dane osobowe (PII), takie jak nazwa użytkownika i hasło nie są rejestrowane w śladach i rejestrowane komunikaty. Administrator komputera, jednak można użyć `enableLoggingKnownPII` atrybutu w `machineSettings` elementu w pliku Machine.config, aby zezwolić aplikacji na maszynie się znane identyfikowalne dane osobowe (PII) w następujący sposób:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` element istnieje poza pliku Machine.config, system generuje <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Zmiany zostaną zastosowane, tylko wtedy, gdy rozpoczyna się lub ponowne uruchomienie aplikacji. Zdarzenie jest rejestrowane podczas uruchamiania, gdy oba atrybuty są ustawione na `true`. Jeśli zdarzenie jest również rejestrowana `logKnownPii` ustawiono `true` , ale `enableLoggingKnownPii` jest `false`.  
  
 Aby uzyskać więcej informacji na temat rejestrowania danych osobowych, zobacz [blokada zabezpieczeń PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) próbki.  
  
 Administrator maszyny i wdrażania aplikacji należy zachować wyjątkową ostrożność, korzystając z tych dwóch przełączników. Jeśli włączono rejestrowanie dane osobowe, kluczy zabezpieczeń i dane osobowe są rejestrowane. Jeśli jest wyłączone, dane poufne i specyficzne dla aplikacji są nadal rejestrowane w wiadomości nagłówki i treść. Bardziej szczegółowe omówienie dotyczące ochrony prywatności i ochrony danych osobowych przed przypadkowym, zobacz [rozwiązania prywatność użytkownika](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
 Ponadto adres IP nadawcy wiadomości jest rejestrowane raz na połączenia dla transportu nawiązaniem połączenia i jeden raz na wiadomością wysłaną w inny sposób. Można to zrobić bez zgody nadawcy. Jednak rejestrowanie występuje tylko na poziomie informacji lub pełne śledzenie, które nie są domyślnie lub zalecane poziomy śledzenia w środowisku produkcyjnym, z wyjątkiem aktywnego debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
