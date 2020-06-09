---
title: Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 0a09e387a4f964441f11d07a84bd492345d5b691
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578880"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
W tym temacie opisano, jak można chronić poufne informacje przed ujawnieniem, a także przydatne porady dotyczące korzystania z programu WebHost.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Korzystanie z niestandardowego odbiornika śledzenia z elementem WebHost  
 Jeśli piszesz własny odbiornik śledzenia, należy mieć świadomość, że ślady mogą zostać utracone w przypadku usługi hostowanej w sieci Web. Podczas odtwarzania programu WebHost zamykany jest proces na żywo, podczas gdy duplikat jest przełączany. Jednak te dwa procesy muszą nadal mieć dostęp do tego samego zasobu przez jakiś czas, który jest zależny od typu odbiornika. W takim przypadku program `XmlWriterTraceListener` tworzy nowy plik śledzenia dla drugiego procesu; podczas gdy śledzenie zdarzeń systemu Windows zarządza wieloma procesami w ramach tej samej sesji i zapewnia dostęp do tego samego pliku. Jeśli własny odbiornik nie oferuje podobnych funkcji, ślady mogą zostać utracone, gdy plik zostanie zablokowany przez dwa procesy.  
  
 Należy również pamiętać, że niestandardowy odbiornik śledzenia może wysyłać ślady i wiadomości w sieci, na przykład do zdalnej bazy danych. Jako narzędzie do wdrażania aplikacji należy skonfigurować odbiorniki niestandardowe z odpowiednią kontrolą dostępu. Należy również zastosować kontrolę zabezpieczeń na wszystkich danych osobowych, które mogą być ujawnione w lokalizacji zdalnej.  
  
## <a name="logging-sensitive-information"></a>Rejestrowanie poufnych informacji  
 Ślady zawierają nagłówki wiadomości, gdy komunikat jest w zakresie. Gdy śledzenie jest włączone, dane osobowe w nagłówkach specyficznych dla aplikacji, takie jak, ciąg zapytania; i informacje o treści, takie jak numer karty kredytowej, mogą stać się widoczne w dziennikach. Narzędzie wdrażania aplikacji jest odpowiedzialne za wymuszanie kontroli dostępu do plików konfiguracji i śledzenia. Jeśli nie chcesz, aby ten rodzaj informacji był widoczny, należy wyłączyć śledzenie lub odfiltrować część danych, jeśli chcesz udostępnić dzienniki śledzenia.  
  
 Poniższe porady mogą pomóc zapobiec przypadkowemu ujawnieniu zawartości pliku śledzenia:  
  
- Upewnij się, że pliki dziennika są chronione za pomocą list Access Control (ACL) zarówno w scenariuszach WebHost, jak i z dowolnego hosta.  
  
- Wybierz rozszerzenie pliku, którego nie można łatwo obsłużyć przy użyciu żądania sieci Web. Na przykład rozszerzenie pliku XML nie jest bezpiecznym wyborem. Aby wyświetlić listę rozszerzeń, które mogą być obsługiwane, można sprawdzić Przewodnik administrowania usługami IIS.  
  
- Określ ścieżkę bezwzględną dla lokalizacji pliku dziennika, która powinna znajdować się poza katalogiem publicznym programu WebHost, aby uniemożliwić dostęp do niego przez zewnętrzną stronę przy użyciu przeglądarki sieci Web.  
  
 Domyślnie klucze i dane osobowe, takie jak nazwa użytkownika i hasło, nie są rejestrowane w śladach i zarejestrowanych komunikatach. Administrator komputera może jednak użyć `enableLoggingKnownPII` atrybutu w `machineSettings` pliku Machine. config, aby zezwolić aplikacjom działającym na komputerze na rejestrowanie znanych danych osobowych (dane osobowe) w następujący sposób:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
  
 Tylko wtedy, gdy oba ustawienia są włączone do rejestrowania przez dane `true` osobowe. Kombinacja dwóch przełączników pozwala elastycznie rejestrować znane dane OSOBowe dla każdej aplikacji.  
  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` element istnieje poza plikiem Machine. config, system zgłasza <xref:System.Configuration.ConfigurationErrorsException> .  
  
 Zmiany są skuteczne tylko wtedy, gdy aplikacja jest uruchamiana lub uruchamiana ponownie. Zdarzenie jest rejestrowane przy uruchamianiu, gdy oba atrybuty są ustawione na `true` . Zdarzenie jest rejestrowane również wtedy, gdy `logKnownPii` jest ustawione na, `true` ale `enableLoggingKnownPii` jest `false` .  
  
 Aby uzyskać więcej informacji na temat rejestrowania danych osobowych, zobacz przykład [blokady zabezpieczeń danych osobowych](../../samples/pii-security-lockdown.md) .  
  
 W przypadku korzystania z tych dwóch przełączników administrator komputera i narzędzie wdrażania aplikacji powinny mieć wyjątkową ostrożność. W przypadku włączenia rejestrowania przez dane OSOBowe są rejestrowane klucze zabezpieczeń i dane OSOBowe. Jeśli jest wyłączona, poufne i specyficzne dla aplikacji dane są nadal rejestrowane w nagłówkach i treściach komunikatów. Aby uzyskać bardziej szczegółowe omówienie ochrony prywatności i ochrony danych osobowych przed ujawnieniem, zobacz [prywatność użytkowników](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
 Ponadto adres IP nadawcy wiadomości jest rejestrowany raz dla połączenia dla transportów zorientowanych na połączenia, a raz na komunikat wysyłany w inny sposób. Jest to wykonywane bez zgody nadawcy. Jednak rejestrowanie odbywa się tylko na poziomach śledzenia informacji lub szczegółowości, które nie są domyślnymi lub zalecanymi poziomami śledzenia w środowisku produkcyjnym, z wyjątkiem debugowania na żywo.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
