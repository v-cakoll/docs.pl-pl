---
title: Używanie klasy Message
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
ms.openlocfilehash: 1db509d8f1c672bf51cac7f1ca6b1af91b34fa4d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591264"
---
# <a name="using-the-message-class"></a>Używanie klasy Message
<xref:System.ServiceModel.Channels.Message> Klasy jest niezbędne do programu Windows Communication Foundation (WCF). Cała komunikacja między klientami i usługami ostatecznie powoduje <xref:System.ServiceModel.Channels.Message> wysyłanych i odbieranych wystąpień.  
  
 Nie będzie zazwyczaj korzystają ze <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio. Zamiast tego WCF service model konstrukcji, takie jak kontrakty danych, kontrakty komunikatów i kontrakty operacji są używane do opisywania wiadomości przychodzących i wychodzących. Jednak w niektórych zaawansowanych scenariuszy można programować za pomocą <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio. Na przykład możesz chcieć użyć <xref:System.ServiceModel.Channels.Message> klasy:  
  
- Gdy będziesz potrzebować alternatywny sposób tworzenia wychodzącego treść wiadomości (na przykład tworzenia komunikatu bezpośrednio z pliku na dysku) zamiast serializacji obiektów .NET Framework.  
  
- Gdy będziesz potrzebować alternatywny sposób za pomocą wiadomości przychodzące (na przykład, jeśli chcesz zastosować transformacji XSLT do nieprzetworzonej zawartości XML) zamiast deserializacji obiektów .NET Framework.  
  
- Gdy zachodzi potrzeba obsługi wiadomości w sposób ogólny, niezależnie od tego, treść wiadomości (na przykład, kiedy routing lub przesyłanie dalej komunikatów podczas kompilowania router, moduł równoważenia obciążenia lub publikowania-subskrypcji systemu).  
  
 Przed rozpoczęciem korzystania z <xref:System.ServiceModel.Channels.Message> klasy, zapoznaj się z architekturą transferu danych WCF w [omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
 Element <xref:System.ServiceModel.Channels.Message> jest kontener ogólnego zastosowania dla danych, ale jej projekt jest ściśle zgodna projektu komunikat protokołu SOAP. Podobnie jak w protokołu SOAP, wiadomość zawiera nagłówki i treść wiadomości. Treść wiadomości zawiera dane rzeczywiste ładunek, gdy nagłówki zawierać kontenery dodatkowych danych o nazwie. Reguły dotyczące odczytywania i zapisywania treści i nagłówki są różne, na przykład nagłówki zawsze są buforowane w pamięci i mogą być dostępne w dowolna kolejność dowolną liczbę razy, gdy jednostka mogą być odczytywane tylko raz i mogą być przesyłane strumieniowo. Normalnie korzystając z protokołu SOAP, treść jest mapowany do treści protokołu SOAP i nagłówków wiadomości są mapowane do nagłówków protokołu SOAP.  
  
## <a name="using-the-message-class-in-operations"></a>Używanie klasy Message w operacjach  
 Możesz użyć <xref:System.ServiceModel.Channels.Message> operacją, zwracana wartość operacji i / lub klasy jako parametr wejściowy. Jeśli <xref:System.ServiceModel.Channels.Message> służy dowolne miejsce w przypadku operacji, obowiązują następujące ograniczenia:  
  
- Operacja nie może zawierać żadnych `out` lub `ref` parametrów.  
  
- Nie może istnieć więcej niż jeden `input` parametru. Jeśli parametr jest obecna, musi to być wiadomość lub typ kontraktu komunikatu.  
  
- Zwracany typ musi być albo `void`, `Message`, lub typ kontraktu komunikatu.  
  
 Poniższy przykład kodu zawiera kontrakt prawidłową operacją.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Tworzenie podstawowego wiadomości  
 <xref:System.ServiceModel.Channels.Message> Klasa udostępnia statyczny `CreateMessage` metodami factory, które służy do tworzenia podstawowych wiadomości.  
  
 Wszystkie `CreateMessage` przeładowania mają parametr wersji typu <xref:System.ServiceModel.Channels.MessageVersion> oznacza to, wersje i SOAP, WS-Addressing dla wiadomości. Jeśli chcesz używać tych samych protokołów jako komunikatu przychodzącego, możesz użyć <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> właściwość <xref:System.ServiceModel.OperationContext> wystąpienia uzyskany z <xref:System.ServiceModel.OperationContext.Current%2A> właściwości. Większość `CreateMessage` przeciążenia również mieć parametr ciągu, który wskazuje Akcja SOAP do użycia dla wiadomości. Można ustawić wersji `None` wyłączenie generowania koperty protokołu SOAP; komunikat składa się tylko treści.  
  
## <a name="creating-messages-from-objects"></a>Tworzenie wiadomości z obiektów  
 Najbardziej podstawowym `CreateMessage` przeciążenia, które przyjmuje tylko wersję i akcji tworzy komunikat o pustej treści. Innego przeciążenia metody ma dodatkowy <xref:System.Object> parameter; spowoduje to utworzenie wiadomości, których treść jest zserializowana reprezentacja danego obiektu. Użyj <xref:System.Runtime.Serialization.DataContractSerializer> przy użyciu ustawień domyślnych dla serializacji. Jeśli chcesz użyć innego serializatora lub chcesz `DataContractSerializer` skonfigurowane inaczej, użyj `CreateMessage` przeciążenia przyjmującego również `XmlObjectSerializer` parametru.  
  
 Na przykład aby zwrócić obiekt w komunikacie, służy poniższy kod.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>Tworzenie wiadomości z czytników XML  
 Istnieją `CreateMessage` przeciążeń przybierają tego <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlDictionaryReader> treści zamiast obiektu. W tym przypadku treść wiadomości zawiera kod XML, będącą wynikiem odczytywanie ich z przekazanych odczytującego XML. Na przykład poniższy kod zwraca komunikat o treści zawartość odczytu z pliku XML.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Ponadto istnieją `CreateMessage` przeciążeń przybierają tego <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlDictionaryReader> reprezentująca cały komunikat i nie tylko treści. Taka przeciążona funkcja sprawdza skorzystać z liczbą całkowitą `maxSizeOfHeaders` parametru. Nagłówki zawsze są buforowane w pamięci jak najszybciej utworzyć wiadomości, a ten parametr ogranicza buforowania, która ma miejsce. Jest to ważne, aby ustawić ten parametr na wartość bezpieczne, gdy plik XML pochodzi z niezaufanego źródła, aby ograniczyć możliwość "odmowa usługi". Wersje i SOAP, WS-Addressing komunikat, który reprezentuje odczytującego XML musi odpowiadać wersji, używając parametru wersji.  
  
## <a name="creating-messages-with-bodywriter"></a>Tworzenie wiadomości za pomocą BodyWriter  
 Jeden `CreateMessage` przeciążenia przyjmuje `BodyWriter` wystąpienia, aby opisać treść komunikatu. Element `BodyWriter` jest klasą abstrakcyjną, jaką można dostosować sposób tworzenia treści wiadomości. Możesz utworzyć swój własny `BodyWriter` klasy, aby opisać treść wiadomości w niestandardowy sposób. Konieczne jest przesłonięcie `BodyWriter.OnWriteBodyContents` metody, która przyjmuje <xref:System.Xml.XmlDictionaryWriter>; ta metoda jest odpowiedzialna za wypisywanie treści.  
  
 Autorzy treść można buforować lub niebuforowanym (przesyłane strumieniowo). Autorzy buforowanego treść można napisać poza ich zawartość dowolną liczbę razy, gdy z nich przesyłane strumieniowo można zapisać ich zawartość tylko raz. `IsBuffered` Właściwość wskazuje, czy edytor treści są buforowane, czy nie. Możesz ustawić dla Twojego edytora treści przez wywołanie metody chronionej `BodyWriter` konstruktora przyjmującego `isBuffered` parametr logiczny. Autorzy treści obsługuje tworzenie Edytor treści buforowaną na Edytor treści niebuforowanym. Można zastąpić `OnCreateBufferedCopy` metodę, aby dostosować ten proces. Domyślnie buforów w pamięci, który zawiera kod XML zwrócony przez `OnWriteBodyContents` jest używany. `OnCreateBufferedCopy` Trwa `maxBufferSize` parametru liczby całkowitej; Jeśli zastąpienie tej metody nie można utworzyć buforów przekracza to maksymalny rozmiar.  
  
 `BodyWriter` Klasa udostępnia `WriteBodyContents` i `CreateBufferedCopy` metody, które są zasadniczo alokowanych otok wokół `OnWriteBodyContents` i `OnCreateBufferedCopy` metod, odpowiednio. Te metody wykonać sprawdzanie stanu, aby upewnić się, że edytor niebuforowanym treść nie jest dostępna więcej niż jeden raz. Te metody są wywoływane bezpośrednio tylko podczas tworzenia niestandardowego `Message` oparte na klasach pochodnych `BodyWriters`.  
  
## <a name="creating-fault-messages"></a>Tworzenie komunikaty o błędach  
 Można użyć pewnych `CreateMessage` przeciążenia, aby utworzyć protokołu SOAP błędów wiadomości. Najbardziej podstawowym te przyjmuje <xref:System.ServiceModel.Channels.MessageFault> obiekt, który opisuje błąd. Dla wygody zapewniono inne przeciążenia. Pierwszy przykład przeciążenia przyjmuje `FaultCode` i ciąg Przyczyna i tworzy `MessageFault` przy użyciu `MessageFault.CreateFault` przy użyciu tych informacji. Inne przeciążenia przyjmuje obiekt zawierający szczegóły i przekazuje go do `CreateFault` wraz z kodem błędu i przyczynę. Na przykład następująca operacja zwraca błąd.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Wyodrębnianie danych treści komunikatu  
 `Message` Klasy obsługuje wiele sposobów wyodrębnianie informacji z jego treści. Te można podzielić na następujące kategorie:  
  
- Pobieranie treści cały komunikat zapisywane tylko raz do edytora XML. Jest to określane jako *zapisania komunikatu*.  
  
- W treści wiadomości, pobieranie odczytującego XML. Dzięki temu można później przechodzi do komunikat o treści —-eliminujemy zgodnie z potrzebami. Jest to określane jako *czytania wiadomości*.  
  
- Cała wiadomość, łącznie z jej treści mogą być kopiowane do buforów w pamięci z <xref:System.ServiceModel.Channels.MessageBuffer> typu. Jest to określane jako *kopiowanie komunikat*.  
  
 Można uzyskać dostęp do treści `Message` tylko raz, niezależnie od tego, jak jest on dostępny. Obiekt komunikatu ma `State` właściwość, która jest początkowo ustawiona Created. Metody dostępu trzy opisane na powyższej liście Ustaw stan Written, Odczyt i skopiowanych, odpowiednio. Ponadto `Close` metody można ustawić stanu na zamknięty, treść wiadomości nie są już wymagane. Treść komunikatu jest możliwy tylko w stanie Created, a nie istnieje sposób, aby powrócić do stanu utworzone po zmianie stanu.  
  
## <a name="writing-messages"></a>Zapisywania komunikatów  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Metoda zapisuje się zawartość treści danego `Message` wystąpienia danego modułu zapisujący XML. <xref:System.ServiceModel.Channels.Message.WriteBody%2A> Metoda działa tak samo, chyba że je otacza element otoki odpowiednią zawartość treści (na przykład <`soap:body`>). Na koniec <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> zapisy na poziomie całej wiadomości, w tym opakowywania SOAP koperty i nagłówki. Jeśli protokołu SOAP jest wyłączona (<xref:System.ServiceModel.Channels.Message.Version> jest <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>), wszystkie trzy metody te same czynności wykonasz: zapisać ich zawartość treści wiadomości.  
  
 Na przykład poniższy kod zapisuje się treść wiadomości przychodzących do pliku.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 Dwie metody pomocnika dodatkowe zapisać niektórych początkowe znaczniki elementu SOAP. Te metody nie uzyskać dostępu do treści wiadomości, a więc nie zmieniają stan komunikatu. Należą do nich następujące elementy:  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A> na przykład zapisuje elementu body start `<soap:Body>`.  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A> Zapisuje element koperty początkowy, na przykład `<soap:Envelope>`.  
  
 Aby napisać końcowego odpowiednie tagi elementów, należy wywołać `WriteEndElement` na odpowiednie edytora XML. Te metody są rzadko wywoływane bezpośrednio.  
  
## <a name="reading-messages"></a>Odczytywanie wiadomości  
 Podstawowym sposobem można odczytać treści komunikatu jest wywołanie <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Możesz wrócić <xref:System.Xml.XmlDictionaryReader> służącego do odczytu treści wiadomości. Należy pamiętać, że <xref:System.ServiceModel.Channels.Message> przechodzi do stanu odczytu zaraz <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> jest wywoływana, i nie kiedy używać zwrócone odczytującego XML.  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> Metoda umożliwia również dostęp do treści wiadomości jako typizowany obiekt. Wewnętrznie ta metoda używa `GetReaderAtBodyContents`, a więc również przejścia stanu komunikatu do <xref:System.ServiceModel.Channels.MessageState.Read> stanu (zobacz <xref:System.ServiceModel.Channels.Message.State%2A> właściwości).  
  
 Jest dobrą praktyką, aby sprawdzić <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> właściwości, w którym treść komunikatu jest pusta i <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> zgłasza <xref:System.InvalidOperationException>. Ponadto jeśli odebranego komunikatu (na przykład odpowiedź), mogą również chcesz sprawdzić <xref:System.ServiceModel.Channels.Message.IsFault%2A>, która wskazuje, czy wiadomość zawiera błąd.  
  
 Najbardziej podstawowa przeciążenia <xref:System.ServiceModel.Channels.Message.GetBody%2A> deserializuje treść komunikatu do wystąpienia typu (wskazywany przez parametr ogólny) przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> skonfigurowanego przy użyciu ustawień domyślnych i <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> przydziału wyłączone. Jeśli chcesz użyć aparatu różnych serializacji lub skonfigurować `DataContractSerializer` w sposób inny niż domyślny, należy użyć <xref:System.ServiceModel.Channels.Message.GetBody%2A> przeciążenia przyjmującego <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 Na przykład, poniższy kod wyodrębnia dane z treści wiadomości, który zawiera Zserializowany obiekt `Person` obiektu i nazwisko osoby do drukowania.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Kopiowanie wiadomość do buforu  
 Czasami jest to konieczne, aby uzyskać dostęp do treści komunikatu więcej niż raz, na przykład, na udostępnianie dalej tego samego komunikatu do wielu miejsc docelowych jako część systemu dla subskrybentów wydawcy. W tym przypadku jest wymagany do buforowania cały komunikat (w tym treść) w pamięci. Można to zrobić, wywołując <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>. Ta metoda przyjmuje parametru liczby całkowitej, która reprezentuje maksymalny rozmiar buforu, a następnie tworzy nie większy niż ten rozmiar buforu. Należy ustawić wartość bezpieczne, jeśli wiadomość pochodzi z niezaufanego źródła.  
  
 Rozmiar buforu jest zwracana jako <xref:System.ServiceModel.Channels.MessageBuffer> wystąpienia. Możesz uzyskać dostęp do danych w buforze na kilka sposobów. Podstawowym sposobem jest wywołanie <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> utworzyć `Message` wystąpień z buforu.  
  
 Innym sposobem uzyskania dostępu do danych w buforze jest zaimplementowanie <xref:System.Xml.XPath.IXPathNavigable> interfejs, który <xref:System.ServiceModel.Channels.MessageBuffer> klasy implementuje bezpośredni dostęp podstawowy kod XML do. Niektóre <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> przeciążenia pozwalają tworzyć <xref:System.Xml.XPath> nawigatorów chronione według przydziału do węzła, ograniczenie liczby węzłów XML, które mogą odwiedzać. Pomaga to zapobiegać atakom typu odmowa usługi na podstawie długiego czasu przetwarzania. Ta oferta jest domyślnie wyłączona. Niektóre `CreateNavigator` przeciążenia pozwalają określić sposób obsługi biały znak w pliku XML przy użyciu <xref:System.Xml.XmlSpace> wyliczenie z są domyślne `XmlSpace.None`.  
  
 Końcowe sposób dostępu do zawartości buforu komunikatu jest napisanie poza swoją zawartość do strumienia z wykorzystaniem <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>.  
  
 W poniższym przykładzie pokazano proces pracy ze `MessageBuffer`: wiadomości przychodzących jest przekazywane do wielu odbiorców, a następnie rejestrowane w pliku. Bez buforowania, nie jest to możliwe, ponieważ treść komunikatu mają dostęp tylko raz.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer` Klasa ma innych członków warte odnotowania. <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> Można wywołać metody aby zwolnić zasoby zawartości buforu nie są już wymagane. <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> Właściwość zwraca rozmiaru przydzielonego buforu. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> Właściwość zwraca typ zawartości MIME wiadomości.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Dostęp do treści wiadomości do debugowania  
 Na potrzeby debugowania, możesz wywołać <xref:System.ServiceModel.Channels.Message.ToString%2A> metodę, aby uzyskać reprezentację komunikatu jako ciąg. Taka reprezentacja ogólnie pasuje do sposobu wiadomość będzie wyglądała na potrzeby przesyłu jeśli jego zostały zakodowane za pomocą kodera tekstu z tą różnicą, że plik XML może być lepiej sformatowane, aby poprawia czytelność dla ludzi. Jedynym wyjątkiem jest treść komunikatu. Treści, które mogą być odczytywane tylko raz, a `ToString` nie zmienia stanu komunikatu. W związku z tym `ToString` metoda może nie móc uzyskać dostęp do treści i może być Zastąp symbol zastępczy (na przykład "..." lub trzy kropki) zamiast treść komunikatu. W związku z tym, nie używaj `ToString` do rejestrowania wiadomości, jeśli ważne jest, treść wiadomości.  
  
## <a name="accessing-other-message-parts"></a>Uzyskiwanie dostępu do innych części wiadomości  
 Różne właściwości znajdują się na dostęp do informacji o wiadomości, innej niż jego zawartość treści. Jednak te nie może być wywoływana po zamknięciu komunikatu:  
  
- <xref:System.ServiceModel.Channels.Message.Headers%2A> Właściwość reprezentuje nagłówki wiadomości. Zobacz sekcję "Praca z nagłówkami" w dalszej części tego tematu.  
  
- <xref:System.ServiceModel.Channels.Message.Properties%2A> Właściwość reprezentuje właściwości wiadomości, które są fragmentów danych o nazwie w załączniku do wiadomości, która nie jest ogólnie Pobierz emitowane po wysłaniu wiadomości. Zobacz sekcję "Praca z właściwości" w dalszej części tego tematu.  
  
- <xref:System.ServiceModel.Channels.Message.Version%2A> Właściwość wskazuje wersję protokołu SOAP i WS-Addressing skojarzonych z wiadomością lub `None` wyłączenie protokołu SOAP.  
  
- <xref:System.ServiceModel.Channels.Message.IsFault%2A> Właściwość zwraca `true` Jeśli komunikat jest komunikatem błędu protokołu SOAP.  
  
- <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> Właściwość zwraca `true` Jeśli komunikat jest pusty.  
  
 Możesz użyć <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> metody dostępu określony atrybut na element otoki treści (na przykład `<soap:Body>`) identyfikowane przez nazwę określonego i przestrzeni nazw. Jeśli nie ma takiego atrybutu, `null` jest zwracana. Ta metoda może być wywoływana tylko wtedy, gdy `Message` jest w stanie Created (Jeśli treść komunikatu nie uzyska dostępu).  
  
## <a name="working-with-headers"></a>Praca z nagłówkami  
 A `Message` może zawierać dowolną liczbę nazwanych fragmenty XML, o nazwie *nagłówki*. Każdy fragment zwykle mapuje nagłówek SOAP. Nagłówki są dostępne za pośrednictwem `Headers` właściwości typu <xref:System.ServiceModel.Channels.MessageHeaders>. <xref:System.ServiceModel.Channels.MessageHeaders> jest kolekcją <xref:System.ServiceModel.Channels.MessageHeaderInfo> obiektów i nagłówki poszczególnych jest możliwy za pośrednictwem jego <xref:System.Collections.IEnumerable> interfejsu lub za pośrednictwem jego indeksatora. Na przykład, poniższy kod wyświetla nazwy wszystkich nagłówków w `Message`.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Dodawanie, usuwanie, wyszukiwanie nagłówki  
 Można dodać nowy nagłówek na końcu wszystkie istniejące nagłówki przy użyciu <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> metody. Możesz użyć <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> metodę, aby wstawić nagłówek pod określonym indeksem. Istniejące nagłówki są przesuwane wstawionego elementu. Nagłówki są uporządkowane według ich indeksu, a pierwszy dostępny indeks to 0. Można użyć różnych <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> przeciążenia metody, aby dodać nagłówków z innego `Message` lub `MessageHeaders` wystąpienia. Niektóre przeciążenia skopiuj jeden nagłówek poszczególnych, podczas gdy inne należy skopiować wszystkie z nich. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> Metoda usuwa wszystkie nagłówki. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> Metoda usuwa nagłówek indeksem określonym (przesunięcie wszystkie nagłówki po nim). <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> Metoda usuwa wszystkie nagłówki o określonej nazwie i przestrzeni nazw.  
  
 Pobrać za pomocą określonego nagłówka <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> metody. Ta metoda przyjmuje nazwę i przestrzeń nazw nagłówka, aby odnaleźć i zwraca jego indeks. Jeśli nagłówek występuje więcej niż jeden raz, jest zgłaszany wyjątek. Jeśli nagłówek nie zostanie znaleziona, zwraca -1.  
  
 W modelu nagłówek SOAP, nagłówki mogą mieć `Actor` wartość, która określa zamierzonym odbiorcą nagłówka. Najbardziej podstawowym `FindHeader` przeciążenia przeszukuje tylko nagłówki przeznaczone dla ultimate odbiorcy wiadomości. Jednak innego przeciążenia metody umożliwia określenie, które `Actor` wartości są uwzględnione w wyszukiwaniu. Aby uzyskać więcej informacji zobacz specyfikację protokołu SOAP.  
  
 A <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> metoda znajduje się do skopiowania nagłówków z <xref:System.ServiceModel.Channels.MessageHeaders> kolekcji do tablicy <xref:System.ServiceModel.Channels.MessageHeaderInfo> obiektów.  
  
 Aby uzyskać dostęp do danych XML w nagłówku, możesz wywołać <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> i zwracają odczytującego XML dla indeksu określonego nagłówka. Do deserializacji zawartości nagłówka do obiektu, należy użyć <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> lub jednego z innych przeciążeniach. Najbardziej podstawowa przeciążenia deserializacji przy użyciu nagłówków <xref:System.Runtime.Serialization.DataContractSerializer> skonfigurowane w domyślnej sposób. Jeśli chcesz użyć innego serializatora lub innej konfiguracji `DataContractSerializer`, użyj jednego z przeciążeń, które przyjmują `XmlObjectSerializer`. Dostępne są także przeciążeń, które przyjmują nazwę nagłówka, przestrzeń nazw i, opcjonalnie, listę `Actor` wartości zamiast indeksu; to jest kombinacją `FindHeader` i `GetHeader`.  
  
## <a name="working-with-properties"></a>Praca z właściwościami  
 A `Message` wystąpienia może zawierać dowolną liczbę nazwane obiekty dowolnego typu. Ta kolekcja jest dostępny za pośrednictwem `Properties` właściwości typu `MessageProperties`. Implementuje kolekcji <xref:System.Collections.Generic.IDictionary%602> interfejs i działa jako mapowanie <xref:System.String> do <xref:System.Object>. Zazwyczaj nie są mapowane bezpośrednio do dowolnej części wiadomości na łączu wartości właściwości, ale raczej zapewnienia różnych komunikatu wskazówek przetwarzania do różnych kanałów w stosie kanału WCF, lub do <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> struktura usługi. Aby uzyskać przykład, zobacz [omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>Dziedziczenie z klasy wiadomości  
 Wbudowany komunikat typy utworzone za pomocą `CreateMessage` nie spełnia Twoje wymagania, Utwórz klasę, która pochodzi od klasy `Message` klasy.  
  
### <a name="defining-the-message-body-contents"></a>Definiowanie treść wiadomości  
 Dla dostępu do danych w ramach treści wiadomości istnieją trzy podstawowe techniki: zapisywanie, odczytywanie i skopiować go do buforu. Te operacje ostatecznie powoduje <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>, i <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> metody wywołanego, odpowiednio, na Twojej klasy pochodnej z `Message`. Podstawa `Message` klasy gwarantuje tylko jeden z tych metod jest wywoływana dla każdego `Message` wystąpienia i że nie jest wywoływany więcej niż jeden raz. Klasa bazowa gwarantuje również, zamknięte komunikatu nie są wywoływane metody. Nie ma potrzeby śledzenia stanu komunikatu w danej implementacji.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> jest metoda abstrakcyjna i muszą być zaimplementowane. Najprostszym sposobem definiowania zawartości w treści wiadomości jest dokonany zapis przy użyciu tej metody. Na przykład następujący komunikat o błędzie zawiera 100 000 losowych liczb z zakresu od 1 do 20.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> i <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> metody mają domyślnej implementacji, które działają w większości przypadków. Wywołania implementacji domyślnej <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, buforować wyniki i pracować z buforu wynikowego. Jednak w niektórych przypadkach to może nie być wystarczająca. W poprzednim przykładzie odczytywanie wiadomości skutkuje 100 000 elementów XML są buforowane, których nie może być pożądane. Możesz chcieć zastąpić <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> do zwrócenia niestandardowego <xref:System.Xml.XmlDictionaryReader> pochodne klasy, która obsługuje liczb losowych. Następnie można zastąpić <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> do użycia czytnika, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> metoda zwróci wartość, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Podobnie, możesz chcieć zastąpić `OnCreateBufferedCopy` do zwrócenia własne `MessageBuffer` klasy pochodnej.  
  
 Oprócz zapewniania zawartość treści wiadomości, klasy pochodne wiadomości jest również przesłonięcie `Version`, `Headers`, i `Properties` właściwości.  
  
 Należy pamiętać, że jeśli tworzysz kopię wiadomości, używana przez kopię nagłówków wiadomości od oryginału.  
  
### <a name="other-members-that-can-be-overridden"></a>Inne elementy członkowskie, które mogą zostać zastąpione  
 Można zastąpić <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, i <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> metody, aby określić, jak tagi początkowe koperty protokołu SOAP, nagłówków protokołu SOAP i element treści protokołu SOAP są zapisywane. Zwykle odpowiadają one `<soap:Envelope>`, `<soap:Header>`, i `<soap:Body>`. Te metody zwykle nie należy zapisywać wartości po podjęciu <xref:System.ServiceModel.Channels.Message.Version> właściwość zwraca <xref:System.ServiceModel.Channels.MessageVersion.None>.  
  
> [!NOTE]
>  Domyślna implementacja klasy `OnGetReaderAtBodyContents` wywołania `OnWriteStartEnvelope` i `OnWriteStartBody` przed wywołaniem `OnWriteBodyContents` i buforowanie wyników. Nagłówki nie są zapisywane w.  
  
 Zastąp <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> metodę, aby zmienić sposób cały komunikat jest tworzony z jego różne elementy. `OnWriteMessage` Metoda jest wywoływana z <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> i z domyślnego <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> implementacji. Należy pamiętać, że zastępowanie <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> nie jest najlepszym rozwiązaniem. Zaleca się zastąpić odpowiednie `On` metod (na przykład <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, i <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Zastąp <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> do zastąpienia, jak Twoje treści komunikatu jest reprezentowana podczas debugowania. Wartość domyślna to do reprezentowania je jako trzy kropki ("..."). Należy pamiętać, że ta metoda może być wywoływana wiele razy, gdy stan komunikatu jest inna niż zamknięte. Implementacja tej metody nigdy nie powinien powodować żadnych działań, które należy wykonać tylko raz (na przykład Odczyt ze strumienia tylko do przodu).  
  
 Zastąp <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> metodę, aby zezwolić na dostęp do atrybutów w elemencie treści protokołu SOAP. Tę metodę można wywołać dowolną liczbę razy, ale `Message` typu podstawowego gwarantuje, że jest on wywoływany tylko, gdy komunikat jest w stanie Created. Sprawdź stan w implementacji nie jest wymagany. Zwraca zawsze wartość domyślną implementację `null`, co oznacza, że nie istnieją żadne atrybuty w elemencie body.  
  
 Jeśli Twoje `Message` obiektu, które należy wykonać wszelkie specjalnej operacji czyszczenia podczas treść komunikatu nie jest już potrzebne, można zastąpić <xref:System.ServiceModel.Channels.Message.OnClose%2A>. Domyślna implementacja nic nie robi.  
  
 `IsEmpty` i `IsFault` właściwości można zastąpić. Domyślnie oba zwracają `false`.
