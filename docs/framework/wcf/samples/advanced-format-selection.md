---
title: Zaawansowane wybieranie formatu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 124bf59f29ff04e643200edf686f79f573937a03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-format-selection"></a>Zaawansowane wybieranie formatu
W tym przykładzie pokazano, jak rozszerzyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST model programowania do obsługi nowych formatów odpowiedzi wychodzącej. Ponadto próbki używa szablonu T4 do zwracania odpowiedzi jako strony XHTML, prezentacja implementowania styl widoku modelu programowania.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Próbki składa się z usługą proste wraz z kodu klienta, który wysyła żądania do usługi.  Usługa obsługuje jednej operacji [WebGet], który ma następujące podpis metody:`Message EchoListWithGet(string list);`  
  
 Gdy klient wysyła żądanie do usługi, zapewnia rozdzielana przecinkami lista elementów z `list` parametr ciągu zapytania i usługa zwraca tej samej listy w jednym z następujących formatów: XML, JSON, Atom, XHTML lub jpeg.  
  
 Format odpowiedzi zwrócona przez usługę wynika najpierw `format` parametr ciągu zapytania, a drugiego przez nagłówek HTTP zaakceptować dostarczone z żądaniem. Jeśli wartość `format` parametr ciągu zapytania jest jednym z powyższych formatów, a następnie odpowiedź jest zwracana w tym formacie. Jeśli `format` ciąg zapytania nie jest obecne, a następnie usługa iterację elementów nagłówka Accept z żądania i zwraca format pierwszego typu zawartości, która obsługuje usługę.  
  
 Zwracany typ operacji jest warto zauważyć. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST model programowania tylko natywnie obsługuje formaty odpowiedzi XML i JSON, gdy operacja zwraca typ inny niż <xref:System.ServiceModel.Channels.Message>. Jednak przy użyciu <xref:System.ServiceModel.Channels.Message> jako typ zwracany dewelopera ma pełną kontrolę nad jak powinien być sformatowany treści komunikatu.  
  
 W przykładzie użyto <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> i <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> metody odpowiednio serializować listy ciągów do wiadomości XML, JSON i ATOM. Format odpowiedzi jpeg <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> metoda jest używana i jest zapisywany obraz do strumienia. Odpowiedź XHTML <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> jest używana wraz ze wstępnie przetworzonych szablonu T4, który składa się z plikiem .TT — i plik CS wygenerowany automatycznie. Plik .TT — umożliwia deweloperom zapisu odpowiedzi w formularzu szablonu, który zawiera zmienne i kontrolowanie struktury. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]T4, zobacz [generowania artefaktów przez przy użyciu szablonów tekstowych](http://go.microsoft.com/fwlink/?LinkId=166023).  
  
 Próbka składa się z własnym hostowana usługa i klient, który jest uruchamiany w ramach aplikacji konsoli. Podczas działania aplikacji konsoli, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.  
  
#### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1.  Otwórz rozwiązanie przykładowej zaawansowane Wybieranie formatu. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator przykładowej może zostać pomyślnie uruchomiony. To zrobić, klikając prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikony, jak i wybieranie **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B Skompiluj rozwiązanie, a następnie naciśnij klawisz Ctrl-F5, aby uruchomić projekt AdvancedFormatSelection aplikacji konsoli bez debugowania. W oknie konsoli zostanie wyświetlony i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi.  
  
3.  Jak działa próbki, klient wysyła żądania do usługi i zapisuje odpowiedzi w oknie konsoli. Zwróć uwagę, różnych formatach odpowiedzi: XML, JSON Atom i XHTML.  
  
4.  Monit następnie przejdź do identyfikatora URI, w którym możesz poprosić o odpowiedzi w formacie JPEG. Otwórz przeglądarkę i przejdź do danego identyfikatora URI.  
  
5.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>Zobacz też
