---
title: "Używanie klasy Message"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 18cb2162712ffac74972ba20a61cd84657685af0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-message-class"></a>Używanie klasy Message
<xref:System.ServiceModel.Channels.Message> Klasy jest niezbędne, aby [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Cała komunikacja między klientami i usługami powoduje w rezultacie <xref:System.ServiceModel.Channels.Message> wysyłanych i odbieranych wystąpień.  
  
 Nie będzie zazwyczaj interakcję z <xref:System.ServiceModel.Channels.Message> bezpośrednio klasa. Zamiast tego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tworzy model usług, takich jak dane kontrakty, kontraktów komunikatu i kontrakty operacji służą do opisywania wiadomości przychodzących i wychodzących. Jednak w niektórych zaawansowane scenariusze można zaprogramować za pomocą <xref:System.ServiceModel.Channels.Message> bezpośrednio klasa. Na przykład możesz chcieć użyć <xref:System.ServiceModel.Channels.Message> klasy:  
  
-   Jeśli wymagane jest alternatywna metoda tworzenia wychodzącego treść wiadomości (na przykład tworzenie wiadomości bezpośrednio z pliku na dysku) zamiast serializacji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiektów.  
  
-   Jeśli wymagane jest alternatywny sposób używania treści komunikatu przychodzącego (na przykład, jeśli chcesz zastosować transformację XSLT do nieprzetworzonej zawartości XML) zamiast deserializacji do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiektów.  
  
-   Jeśli musisz postępowania w przypadku komunikatów w sposób ogólny, niezależnie od zawartości komunikatu (na przykład, gdy routingu lub przesyłanie komunikatów dalej podczas kompilowania router, usługi równoważenia obciążenia lub publikowanie-subskrypcji systemu).  
  
 Przed użyciem <xref:System.ServiceModel.Channels.Message> klasy, warto zapoznać się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transferu danych architektura [omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
 A <xref:System.ServiceModel.Channels.Message> jest kontenerem ogólnego przeznaczenia dla danych, ale jego projekt jest ściśle zgodna projektowania komunikatu protokołu SOAP. Podobnie jak w SOAP, wiadomość ma zarówno treści wiadomości i nagłówków. Treść wiadomości zawiera danych ładunku rzeczywiste, gdy nagłówki zawierać kontenery dodatkowych danych o podanej nazwie. Reguły do odczytu i zapisu treści i nagłówki są różne, na przykład nagłówki zawsze są buforowane w pamięci i mogą być używane w dowolna kolejność dowolną liczbę razy, gdy jednostka mogą być odczytywane tylko raz i mogą być przesyłane strumieniowo. Zwykle podczas korzystania z protokołu SOAP, treść komunikatu jest mapowana do treści protokołu SOAP, a nagłówki komunikatów są mapowane na nagłówków protokołu SOAP.  
  
## <a name="using-the-message-class-in-operations"></a>Używanie klasy Message podczas wykonywania operacji  
 Można użyć <xref:System.ServiceModel.Channels.Message> klasy jako parametr wejściowy działania, wartość zwracana operacji lub oba. Jeśli <xref:System.ServiceModel.Channels.Message> służy dowolne miejsce w przypadku operacji, obowiązują następujące ograniczenia:  
  
-   Operacja nie ma żadnych `out` lub `ref` parametrów.  
  
-   Nie może istnieć więcej niż jedna `input` parametru. Jeśli parametr jest obecny, musi to być komunikatu lub typ kontraktu komunikatu.  
  
-   Zwracany typ musi być albo `void`, `Message`, lub typ kontraktu komunikatu.  
  
 Poniższy przykład kodu zawiera kontrakt prawidłową operacją.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Tworzenie podstawowych wiadomości  
 <xref:System.ServiceModel.Channels.Message> Klasa udostępnia static `CreateMessage` metodami factory, które służy do tworzenia podstawowych wiadomości.  
  
 Wszystkie `CreateMessage` przeciążenia zająć wersji parametr typu <xref:System.ServiceModel.Channels.MessageVersion> wskazujące SOAP i WS-Addressing wersji dla wiadomości. Jeśli chcesz użyć tej samej wersji protokołu jako komunikat przychodzący, możesz użyć <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> właściwość <xref:System.ServiceModel.OperationContext> wystąpienia uzyskane z <xref:System.ServiceModel.OperationContext.Current%2A> właściwości. Większość `CreateMessage` overloads ma także parametr typu string, która wskazuje akcji SOAP dla komunikatu. Wersja może być ustawiony na `None` wyłączenie generowania koperty protokołu SOAP; komunikat składa się tylko treści.  
  
## <a name="creating-messages-from-objects"></a>Tworzenie wiadomości z obiektów  
 Najprostsza `CreateMessage` przeciążenia, które przyjmuje tylko wersję i akcji, tworzy komunikat o pustej treści. Innego przeciążenia przyjmuje dodatkowych <xref:System.Object> parametru; spowoduje to utworzenie wiadomości, których treść jest zserializowana reprezentacja danego obiektu. Użyj <xref:System.Runtime.Serialization.DataContractSerializer> przy użyciu ustawień domyślnych dla serializacji. Jeśli chcesz użyć innego serializatora, lub `DataContractSerializer` inaczej skonfigurowana, użyj `CreateMessage` przeciążenia, które również przyjmuje `XmlObjectSerializer` parametru.  
  
 Na przykład aby zwrócić obiekt w wiadomości, można użyć poniższego kodu.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>Tworzenie wiadomości z czytników XML  
 Brak `CreateMessage` overloads które trwają <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlDictionaryReader> dla treści zamiast obiektu. W takim przypadku treść wiadomości zawiera kod XML, który jest wynikiem odczytu z czytnika XML przekazany. Na przykład następujący kod zwraca komunikat o treści zawartość odczytu z pliku XML.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Ponadto istnieją `CreateMessage` overloads które trwają <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlDictionaryReader> reprezentująca cały komunikat i nie tylko treści. Te przeciążenia również wziąć całkowitą `maxSizeOfHeaders` parametru. Nagłówki są zawsze buforowane w pamięci natychmiast utworzyć wiadomości i ten parametr ogranicza to czas buforowania, która ma miejsce. Jest ważne, aby ustawić ten parametr na wartość bezpieczne, gdy plik XML pochodzi z niezaufanego źródła Aby ograniczyć możliwość odmowy usługi. Wersji protokołu SOAP i WS-Addressing komunikat, który reprezentuje modułu odczytującego XML musi odpowiadać wersji, używając parametru wersji.  
  
## <a name="creating-messages-with-bodywriter"></a>Tworzenie wiadomości z BodyWriter  
 Jeden `CreateMessage` przeciążenia przyjmuje `BodyWriter` wystąpienie do opisywania treści wiadomości. A `BodyWriter` jest klasą abstrakcyjną, jaką można dostosować sposób tworzenia treści wiadomości. Utwórz swój własny `BodyWriter` klasy do opisywania treści wiadomości w niestandardowy sposób. Konieczne jest przesłonięcie `BodyWriter.OnWriteBodyContents` metody pobierającej <xref:System.Xml.XmlDictionaryWriter>; ta metoda jest odpowiedzialna za wypisywanie treści.  
  
 Można buforować treść zapisywania lub niebuforowanym (przesyłane strumieniowo). Autorzy buforowanego treści można zapisać poza ich zawartość dowolną liczbę razy, gdy przesyłany strumieniowo z nich może zapisywać tylko raz poza ich zawartość. `IsBuffered` Właściwość wskazuje, czy edytor treści są buforowane, czy nie. Możesz ustawić dla Twojego zapisu treści przez wywołanie metody chronionej `BodyWriter` konstruktora przyjmującego `isBuffered` parametrów typu boolean. Autorzy treści obsługuje tworzenie Edytor treści buforowanego Autor niebuforowanym treści. Można zastąpić `OnCreateBufferedCopy` metodę w celu dostosowania tego procesu. Domyślnie buforów w pamięci, który zawiera kod XML zwrócony przez `OnWriteBodyContents` jest używany. `OnCreateBufferedCopy`Trwa `maxBufferSize` parametru liczby całkowitej; razie przesłonięcia tej metody nie można utworzyć buforów przekracza dopuszczalny rozmiar.  
  
 `BodyWriter` Klasa udostępnia `WriteBodyContents` i `CreateBufferedCopy` metody, które są zasadniczo elastycznej otoki wokół `OnWriteBodyContents` i `OnCreateBufferedCopy` metod, odpowiednio. Te metody sprawdzania stanu aby upewnić się, że edytor niebuforowanym treści nie jest dostępny więcej niż raz. Te metody są wywoływane bezpośrednio tylko podczas tworzenia niestandardowego `Message` na podstawie klasy pochodne `BodyWriters`.  
  
## <a name="creating-fault-messages"></a>Tworzenie komunikatów "Fault"  
 Można korzystać z pewnych `CreateMessage` przeciążenia, aby utworzyć SOAP fault wiadomości. Najprostsza te przyjmuje <xref:System.ServiceModel.Channels.MessageFault> obiekt, który zawiera opis błędu. Dla wygody zapewniono inne przeciążenia. Pierwszy takie przeciążenia przyjmuje `FaultCode` i ciąg Przyczyna i tworzy `MessageFault` przy użyciu `MessageFault.CreateFault` korzystając z tych informacji. Inne przeciążenia obiekt szczegółów i przekazuje ją do `CreateFault` wraz z kodu błędu i przyczyny. Na przykład następująca operacja zwraca błąd.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Wyodrębnianie danych z treści wiadomości  
 `Message` Klasa obsługuje wiele sposobów wyodrębniania informacji z jego treści. Te można podzielić na następujące kategorie:  
  
-   Pobieranie treści cały komunikat jednocześnie zapisywany do edytora XML. Jest to określane jako *pisanie wiadomości*.  
  
-   Pobieranie modułu odczytującego XML w treści wiadomości. Pozwala to nowsze dostępu komunikat treści element za fragment zgodnie z potrzebami. Jest to określane jako *odczytywania komunikatu*.  
  
-   Cały komunikat, łącznie z jej treści mogą być kopiowane do buforów w pamięci z <xref:System.ServiceModel.Channels.MessageBuffer> typu. Jest to określane jako *kopiowanie komunikat*.  
  
 Można uzyskać dostęp do treści `Message` tylko jeden raz, niezależnie od tego, jaki jest dostępny. Obiekt wiadomości ma `State` właściwość, która jest początkowo ustawiona utworzony. Metody dostępu trzy opisane w powyższej listy Ustaw stan Written, Odczyt i skopiowanych, odpowiednio. Ponadto `Close` metody można ustawić stanu na zamknięty, gdy treść wiadomości nie są już wymagane. Treść komunikatu jest możliwy tylko w stanie Created, a nie istnieje sposób, aby powrócić do jego stan to utworzony po zmianie stanu.  
  
## <a name="writing-messages"></a>Pisanie wiadomości  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Metoda zapisuje się zawartość treści danego `Message` wystąpienia danego edytora XML. <xref:System.ServiceModel.Channels.Message.WriteBody%2A> Metody jest taki sam, z tą różnicą, że go otacza zawartość treści element otoki odpowiednie (na przykład <`soap:body`>). Na koniec <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> zapisy limit całej wiadomości, w tym opakowywania SOAP koperty i nagłówki. Jeśli SOAP jest wyłączone (wersja jest `MessageVersion.None`), wszystkie trzy metody tak samo postąpić: zapisują poza zawartość treści wiadomości.  
  
 Na przykład następujący kod zapisuje się treści wiadomości przychodzących do pliku.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 Dwie metody pomocnicze dodatkowe zapisać niektórych początkowe tagi elementu SOAP. Tych metod nie uzyskać dostępu do treści wiadomości i dlatego nie zmienić stan komunikatu. Należą do nich następujące elementy:  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A>Zapisuje element body początkowy, na przykład `<soap:Body>`.  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A>Zapisuje element koperty początkowy, na przykład `<soap:Envelope>`.  
  
 Aby napisać odpowiedniego końca znaczniki elementów, należy wywołać `WriteEndElement` na odpowiedniego edytora XML. Te metody są rzadko wywołać bezpośrednio.  
  
## <a name="reading-messages"></a>Odczytywanie wiadomości  
 Podstawowy sposobem odczytu treści wiadomości jest wywołać <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Możesz wrócić <xref:System.Xml.XmlDictionaryReader> można odczytać treści wiadomości. Należy pamiętać, że <xref:System.ServiceModel.Channels.Message> przejścia do stanu odczytu natychmiast <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> jest wywoływana, i nie kiedy używać zwrócony modułu odczytującego XML.  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> Metoda umożliwia również dostęp do treści komunikatu jako obiekt typu. Wewnętrznie ta metoda używa `GetReaderAtBodyContents`, a więc także przejścia stanu komunikat do <xref:System.ServiceModel.Channels.MessageState.Read> stanu (zobacz <xref:System.ServiceModel.Channels.Message.State%2A> właściwości).  
  
 Dobrym rozwiązaniem do sprawdzenia jest <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> właściwości, w których przypadku treść komunikatu jest pusta i <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> zgłasza <xref:System.InvalidOperationException>. Ponadto jeśli odebranego komunikatu (na przykład odpowiedzi), może również chcesz sprawdzić <xref:System.ServiceModel.Channels.Message.IsFault%2A>, która wskazuje, czy wiadomość zawiera błąd.  
  
 Najbardziej podstawowa przeciążenia <xref:System.ServiceModel.Channels.Message.GetBody%2A> deserializuje treść komunikatu do wystąpienia typu (wskazywanym przez parametr ogólny), używając <xref:System.Runtime.Serialization.DataContractSerializer> skonfigurowane przy użyciu ustawień domyślnych i z <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> przydziału wyłączone. Jeśli chcesz użyć aparatu różnych serializacji lub skonfiguruj `DataContractSerializer` w sposób inny niż domyślny, za pomocą <xref:System.ServiceModel.Channels.Message.GetBody%2A> przeciążenia, które przyjmuje <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 Na przykład następujący kod wyodrębnia dane z treści wiadomości, który zawiera seryjnych `Person` obiektu i nazwisko osoby do drukowania.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Kopiowanie wiadomości do buforu  
 Czasami jest to konieczne, aby uzyskać dostęp do treści wiadomości więcej niż raz, na przykład, aby przesłać ten sam komunikat do wielu miejsc docelowych jako część systemu subskrybentów wydawcy. W takim przypadku jest wymagany do buforowania w pamięci cały komunikat (w tym treści). Można to zrobić przez wywołanie metody <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>. Ta metoda przyjmuje parametr liczba całkowita, który reprezentuje maksymalny rozmiar buforu, a następnie tworzy nie większy niż rozmiar buforu. Jest ważne, aby ustawić to bezpieczne wartości, gdy komunikat pochodzi z niezaufanego źródła.  
  
 Bufor jest zwracana jako <xref:System.ServiceModel.Channels.MessageBuffer> wystąpienia. Można uzyskać dostępu do danych w buforze na kilka sposobów. Jest podstawowym narzędziem do wywołania <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> utworzyć `Message` wystąpień z buforu.  
  
 Inny sposób uzyskać dostęp do danych w buforze jest zaimplementowanie <xref:System.Xml.XPath.IXPathNavigable> interfejs, który <xref:System.ServiceModel.Channels.MessageBuffer> implementuje bezpośredni dostęp do źródłowego pliku XML do klasy. Niektóre <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> przeciążenia pozwalają tworzyć <xref:System.Xml.XPath> nawigatorów chronione przez przydziału węzła, ogranicza liczbę węzłów XML, które mogą odwiedzać. Pomaga to zapobiec atakom DOS na podstawie długiego czasu przetwarzania. Ta oferta jest domyślnie wyłączona. Niektóre `CreateNavigator` przeciążenia umożliwiają określenie obsługi biały znak w pliku XML przy użyciu <xref:System.Xml.XmlSpace> wyliczenie z są domyślne `XmlSpace.None`.  
  
 Końcowe sposób dostępu do zawartości bufor komunikatów jest napisanie poza swoją zawartość przy użyciu strumienia <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>.  
  
 W poniższym przykładzie pokazano proces pracy ze `MessageBuffer`: wiadomości przychodzącej jest przekazywane do wielu adresatów, a następnie rejestrowane w pliku. Bez buforowania, nie jest to możliwe, ponieważ treść komunikatu mają dostęp tylko raz.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer` Klasa ma innych członków warto zauważyć. <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> Może zostać wywołana metoda aby zwolnić zasoby, gdy zawartość buforu nie są już wymagane. <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> Właściwość zwraca rozmiar buforu przydzielone. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> Właściwość zwraca typ zawartości MIME komunikatu.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Dostęp do treści wiadomości do debugowania  
 Na potrzeby debugowania, możesz wywołać <xref:System.ServiceModel.Channels.Message.ToString%2A> metody, aby uzyskać reprezentację komunikatu jako ciąg. Taka reprezentacja zazwyczaj zgodny komunikat czy wygląd umieszczonego w jeśli jego zostały zakodowane za pomocą kodera tekstu z tą różnicą, że XML byłyby lepiej formatowane dla człowieka czytelności. Jedynym wyjątkiem jest treść komunikatu. Treść, które mogą być odczytywane tylko raz i `ToString` nie zmienia stan komunikatu. W związku z tym `ToString` metoda może nie móc uzyskać dostęp do treści i może Zastąp symbol zastępczy (na przykład "..." lub trzy kropki) zamiast treść komunikatu. W związku z tym nie należy używać `ToString` rejestrować komunikatów, jeśli ważne jest zawartości w treści wiadomości.  
  
## <a name="accessing-other-message-parts"></a>Uzyskiwanie dostępu do innych części wiadomości  
 Dostęp do informacji o komunikacie innego niż jego zawartość treści znajdują się różne właściwości. Jednak te nie można wywołać po zamknięciu komunikat:  
  
-   <xref:System.ServiceModel.Channels.Message.Headers%2A> Właściwość reprezentuje nagłówki komunikatów. Zobacz sekcję "Praca z nagłówkami" w dalszej części tego tematu.  
  
-   <xref:System.ServiceModel.Channels.Message.Properties%2A> Właściwość reprezentuje właściwości wiadomości, które są fragmentów danych o nazwie dołączony do wiadomości, które nie ogólnie uzyskać wysyłanego po wysłaniu wiadomości. Zobacz sekcję "Praca z właściwości" w dalszej części tego tematu.  
  
-   <xref:System.ServiceModel.Channels.Message.Version%2A> Właściwość wskazuje wersję protokołu SOAP i WS-Addressing skojarzony z komunikatem, lub `None` wyłączenie protokołu SOAP.  
  
-   <xref:System.ServiceModel.Channels.Message.IsFault%2A> Zwraca `true` Jeśli komunikat jest komunikatem błędu protokołu SOAP.  
  
-   <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> Zwraca `true` Jeśli komunikat jest pusty.  
  
 Można użyć <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> metodę, aby uzyskać dostępu do określonego atrybutu na element otoki treści (na przykład `<soap:Body>`) identyfikowana na podstawie określonej nazwy i przestrzeni nazw. Jeśli nie odnaleziono takiego atrybutu, `null` jest zwracany. Tę metodę można wywołać tylko wtedy, gdy `Message` jest w stanie Created (Jeśli treść komunikatu nie uzyska dostępu).  
  
## <a name="working-with-headers"></a>Praca z nagłówkami  
 A `Message` może zawierać dowolną liczbę fragmenty XML o nazwie, o nazwie *nagłówki*. Każdy fragment zwykle mapuje do nagłówka SOAP. Nagłówki są dostępne za pośrednictwem `Headers` właściwości typu <xref:System.ServiceModel.Channels.MessageHeaders>. <xref:System.ServiceModel.Channels.MessageHeaders>to kolekcja <xref:System.ServiceModel.Channels.MessageHeaderInfo> obiektów i poszczególne nagłówki są dostępne za pośrednictwem jego <xref:System.Collections.IEnumerable> interfejsu lub za pośrednictwem jego indeksatora. Na przykład poniższy kod wyświetla nazwy wszystkich nagłówków w `Message`.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Dodawanie, usuwanie, wyszukiwanie nagłówki  
 Można dodać nowy nagłówek na końcu wszystkie istniejące nagłówki przy użyciu <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> metody. Można użyć <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> do wstawienia nagłówka od określonego indeksu. Istniejące nagłówki są przesuwane wstawionego elementu. Nagłówki są uporządkowane według ich indeksu i pierwszy dostępny indeks 0. Można użyć różnych <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> przeciążenia metody dodawania nagłówków z inną `Message` lub `MessageHeaders` wystąpienia. Niektóre przeciążenia skopiować jeden nagłówek poszczególnych, podczas gdy inne skopiuj je wszystkie. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> Metoda usuwa wszystkie nagłówki. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> Metoda usuwa nagłówek od określonego indeksu (przesunięcie wszystkich nagłówków po nim). <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> Metoda usuwa wszystkie nagłówki o określonej nazwie i przestrzeni nazw.  
  
 Pobrać za pomocą określonego nagłówka <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> metody. Ta metoda przyjmuje nazwę i przestrzeń nazw nagłówka, aby znaleźć i zwraca jego indeksu. Jeśli w nagłówku występuje więcej niż raz, jest zwracany wyjątek. Jeśli w nagłówku nie zostanie znaleziony, zwraca -1.  
  
 W modelu nagłówka SOAP, może mieć nagłówków `Actor` wartość, która określa adresata nagłówka. Najprostsza `FindHeader` przeciążenia wyszukuje tylko nagłówki przeznaczonych do ostatecznej odbiorcy wiadomości. Jednak innego przeciążenia umożliwia określenie, które `Actor` wartości są uwzględniane w wyszukiwaniu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]Specyfikacja protokołu SOAP.  
  
 A <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> metody są dostarczane do kopiowania nagłówków z <xref:System.ServiceModel.Channels.MessageHeaders> kolekcji do tablicy <xref:System.ServiceModel.Channels.MessageHeaderInfo> obiektów.  
  
 Aby uzyskać dostęp do danych XML w nagłówku, można wywołać <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> i zwracać modułu odczytującego XML dla indeksu określonego nagłówka. Aby deserializować zawartość nagłówka do obiektu, należy użyć <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> lub jednego z innych przeciążeniach. Najbardziej podstawowa przeciążeń deserializacji nagłówków przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> skonfigurowane w domyślnej sposób. Jeśli chcesz użyć innego serializatora lub innej konfiguracji `DataContractSerializer`, użyj jednego z przeciążeń, które przyjmują `XmlObjectSerializer`. Dostępne są także przeciążeń, które przyjmują nazwa nagłówka, przestrzeń nazw i opcjonalnie listę `Actor` wartości zamiast indeksu; jest kombinacją `FindHeader` i `GetHeader`.  
  
## <a name="working-with-properties"></a>Praca z właściwościami  
 A `Message` wystąpienia może zawierać dowolną liczbę nazwane obiekty dowolnego typu. Ta kolekcja jest dostępny za pośrednictwem `Properties` właściwości typu `MessageProperties`. Implementuje kolekcji <xref:System.Collections.Generic.IDictionary%602> interfejsu i działa jako mapowanie <xref:System.String> do <xref:System.Object>. Zazwyczaj nie mapują bezpośrednio do dowolnej części komunikatu umieszczonego w wartości właściwości, ale raczej udostępnia różne wskazówek przetwarzania wiadomości dla różnych kanałów w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanału stosu lub <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> struktura usługi. Na przykład zobacz [omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>Dziedziczenie z klasy wiadomości  
 Jeśli wbudowane komunikatu typy utworzone za pomocą `CreateMessage` nie spełniają wymagania, Utwórz klasę pochodną `Message` klasy.  
  
### <a name="defining-the-message-body-contents"></a>Definiowanie treść wiadomości  
 Istnieją trzy metody głównej do uzyskiwania dostępu do danych w ramach treści wiadomości: zapisywanie, odczytywanie i skopiować go do buforu. Te operacje, ale ostatecznie spowodować <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>, i <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> metody wywoływane, odpowiednio w klasie pochodnej z `Message`. Podstawowym `Message` klasy gwarantuje tylko jeden z tych metod jest wywoływana dla każdej `Message` wystąpienia i że nie jest wywoływany więcej niż raz. Klasa podstawowa gwarantuje również, że metody nie są wywoływane na zamkniętym wiadomości. Nie istnieje potrzeba śledzenia stanu komunikat w implementacji.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>jest metoda abstrakcyjna i musi zostać wdrożone. Najprostszym sposobem definiowania zawartości w treści wiadomości jest przy użyciu tej metody. Na przykład następujący komunikat zawiera 100 000 losowych liczb z zakresu od 1 do 20.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 `OnGetReaderAtBodyContents` i `OnCreateBufferedCopy` metody mają implementacje domyślne, które działają w większości przypadków. Wywołanie implementacji domyślnej `OnWriteBodyContents`wyników buforowania i pracować z buforu wynikowego. Jednak w niektórych przypadkach może to nie być wystarczającej ilości. W poprzednim przykładzie odczytywanie wiadomości skutkuje 100 000 elementów XML są buforowane, które nie może być pożądane. Należy zastąpić `OnGetReaderAtBodyContents` do zwracania niestandardowego `XmlDictionaryReader` klasy pełniącą zapasowej liczb losowych. Następnie można zastąpić `OnWriteBodyContents` do używania czytnika który `OnGetReaderAtBodyContents` zwraca właściwości, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Podobnie, należy zastąpić `OnCreateBufferedCopy` do zwrócenia własne `MessageBuffer` klasy.  
  
 Oprócz zapewnienia treść wiadomości, musi także zastępować klasy komunikat pochodzi `Version`, `Headers`, i `Properties` właściwości.  
  
 Należy zauważyć, że jeśli tworzysz kopię wiadomości kopii używa nagłówki komunikatów z oryginalnego.  
  
### <a name="other-members-that-can-be-overridden"></a>O innych elementach członkowskich, które mogą zostać zastąpione  
 Można zastąpić <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, i <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> metod, aby określić, jak tagi początkowe koperty protokołu SOAP, nagłówki SOAP i elementu treści protokołu SOAP są zapisywane. Zwykle odpowiadają one `<soap:Envelope>`, `<soap:Header>`, i `<soap:Body>`. Te metody zwykle nie należy zapisać niczego czy `Version` zwraca właściwość `MessageVersion.None`.  
  
> [!NOTE]
>  Domyślna implementacja `OnGetReaderAtBodyContents` wywołania `OnWriteStartEnvelope` i `OnWriteStartBody` przed wywołaniem `OnWriteBodyContents` i wyników buforowania. Nagłówki nie są zapisywane.  
  
 Zastąpienie <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> metodę, aby zmienić sposób cały komunikat jest tworzony z jego różnych części. `OnWriteMessage` Metoda jest wywoływana z <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> i domyślnego <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> implementacji. Należy pamiętać, że zastępowanie <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> nie jest najlepszym rozwiązaniem. Zaleca się zastąpienie odpowiednie `On` metody (na przykład <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, i <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Zastąpienie <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> do zastąpienia, jak treść wiadomości są reprezentowane podczas debugowania. Wartość domyślna to do reprezentowania go jako trzy kropki ("..."). Należy pamiętać, że tę metodę można wywoływać wielokrotnie podczas stan komunikatu jest inna niż zamknięte. Implementacja tej metody nigdy nie powinno powodować dowolną akcję, która musi zostać wykonana tylko raz (na przykład Odczyt ze strumienia tylko do przodu).  
  
 Zastąpienie <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> metodę, aby zezwolić na dostęp do atrybutów w elemencie treści protokołu SOAP. Tę metodę można wywołać dowolną liczbę razy, ale `Message` typu podstawowego gwarantuje, że jest on wywoływany tylko, gdy komunikat jest w stanie Created. Sprawdź stan w implementacji nie jest wymagane. Domyślna implementacja zawsze zwraca `null`, co oznacza, że istnieją żadne atrybuty w elemencie body.  
  
 Jeśli Twoje `Message` obiektu należy wykonać specjalne oczyszczania podczas treść komunikatu nie jest już potrzebne, można zastąpić <xref:System.ServiceModel.Channels.Message.OnClose%2A>. Domyślna implementacja nie działa.  
  
 `IsEmpty` i `IsFault` właściwości może zostać zastąpiona. Domyślnie zwrócą `false`.
