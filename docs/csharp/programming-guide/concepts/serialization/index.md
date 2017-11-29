---
title: Serializacja (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 704ff2bf-02ab-4fea-94ea-594107825645
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b045f092bef837d1345b5f3b31df0a5ec22fc010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="serialization-c-"></a>Serializacja (C#)
Serializacja jest proces konwersji obiektu do strumienia bajtów, aby można było zapisać obiekt i przekazuje je do pamięci, bazą danych lub pliku. Głównym celem jest zapisanie stanu obiektu, aby można było utworzyć ją w razie potrzeby ponownie. Odwrotnej proces jest nazywany deserializacji.  
  
## <a name="how-serialization-works"></a>Jak działa serializacji  
 Ta ilustracja przedstawia proces serializacji.  
  
 ![Grafika przedstawiająca serializację](../../../../csharp/programming-guide/concepts/serialization/media/serialization.gif "szeregowanie")  
  
 Strumień, który niesie nie tylko dane, ale informacje o typie obiektu, takie jak jego nazwa wersji, kultury i zestawu serializowany jest obiekt. W strumieniu mogą być przechowywane w bazie danych, plik lub pamięci.  
  
### <a name="uses-for-serialization"></a>Używa do serializacji  
 Serializacja umożliwia deweloperowi zapisanie stanu obiektu i utwórz go ponownie zgodnie z potrzebami, przeznaczone do przechowywania obiektów, jak również wymiany danych. Za pomocą serializacji, deweloper można wykonać akcji, takich jak wysyłanie obiektu do aplikacji zdalnej przy użyciu usługi sieci Web, przekazanie obiektu z jednej domeny do innej, przekazywanie przez zaporę obiektu jako ciąg XML lub zabezpieczenie lub informacje specyficzne dla użytkownika w aplikacjach.  
  
### <a name="making-an-object-serializable"></a>Wprowadzenie do serializacji obiektu  
 Szeregowania obiektu, należy na można zserializować obiektu strumienia zawiera Zserializowany obiekt oraz a <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization>zawiera klasy, które są niezbędne do serializacji i deserializacji obiektów.  
  
 Zastosuj <xref:System.SerializableAttribute> atrybut do typu, aby wskazać, że wystąpień tego typu może być Zserializowany. A <xref:System.Runtime.Serialization.SerializationException> jest zgłaszany wyjątek, jeśli próba serializować, ale nie ma typu <xref:System.SerializableAttribute> atrybutu.  
  
 Jeśli nie chcesz pole w klasie jako możliwy do serializacji, zastosuj <xref:System.NonSerializedAttribute> atrybutu. Jeśli pole typu umożliwiającego serializację zawiera wskaźnik, dojście lub niektóre inne struktura danych, która jest specyficzna dla danego środowiska, a pole nie może uzyskać wiarygodny odtworzenia w innym środowisku, może być dokonanie nonserializable.  
  
 Jeśli serializacji klasa zawiera odwołania do obiektów na innych klas, które są oznaczone jako <xref:System.SerializableAttribute>, również będą wykonywane szeregowo tych obiektów.  
  
## <a name="binary-and-xml-serialization"></a>Binarne i serializacja XML  
 Można użyć pliku binarnego lub serializacji XML. W serializacji binarnej wszystkie elementy członkowskie, nawet te, które są tylko do odczytu są serializowane i zwiększa wydajność. Serializacja XML zawiera czytelność kodu, a także większą elastyczność użycia na współdziałanie i udostępniania obiektów.  
  
### <a name="binary-serialization"></a>Serializacja binarna  
 Serializacja binarna używa kodowania binarnego do generowania compact serializacji dla zastosowań, takich jak pamięci masowej lub sieci opartych na gniazda strumieni.  
  
### <a name="xml-serialization"></a>Serializacji XML  
 Serializacja XML serializuje publiczne pola i właściwości obiektu lub parametrów i zwracanych wartościach metod, w strumieniu XML, które odpowiada określonego dokumentu schematu XML definition language (XSD). Wyniki serializacji XML w silnie typizowane klas z właściwości publiczne i pola, które są konwertowane na XML. <xref:System.Xml.Serialization>zawiera klasy, które są niezbędne do serializacji i deserializacji XML.  
  
 Atrybuty można zastosować do klasy i elementów członkowskich klasy, aby kontrolować sposób <xref:System.Xml.Serialization.XmlSerializer> serializuje i deserializuje wystąpienia klasy.  
  
## <a name="basic-and-custom-serialization"></a>Serializacja podstawowych i niestandardowych  
 Serializacja można przeprowadzić na dwa sposoby podstawowych i niestandardowych. Podstawowe serializacji używa programu .NET Framework, aby automatycznie serializacji obiektu.  
  
### <a name="basic-serialization"></a>Podstawowe serializacji  
 Jedynym wymaganiem w serializacji podstawowa jest, że obiekt ma <xref:System.SerializableAttribute> atrybut zastosowany. <xref:System.NonSerializedAttribute> Można zapobiec serializowana określonych pól.  
  
 Użycie podstawowe serializacji, przechowywanie wersji obiektów może spowodować problemy, w tym przypadku może być preferowana niestandardowej serializacji. Serializacja podstawowa jest najprostszym sposobem wykonania serializacji, ale nie zapewnia poziom kontroli nad procesem.  
  
### <a name="custom-serialization"></a>Niestandardowej serializacji  
 W niestandardowej serializacji można określić dokładnie obiekty, które będą serializowane i jak będą wykonywane. Klasy muszą być oznaczone jako <xref:System.SerializableAttribute> i wdrożenie <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
 Obiektu do zdeserializowania w niestandardowy sposób również, należy użyć niestandardowego konstruktora.  
  
## <a name="designer-serialization"></a>Serializacja projektanta  
 Serializacja projektanta jest specjalna forma serializacji, która obejmuje rodzaj obiektu trwałości zwykle skojarzone z narzędziami programistycznymi. Projektanta serializacji to proces konwertowania z wykresu obiektu na plik źródłowy, który później mogą być używane do odzyskania wykres obiektu. Plik źródłowy może zawierać kod, znaczników lub nawet informacji o tabeli SQL.  
  
##  <a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady  
 [Wskazówki: Przechowywanie obiektu w programie Visual Studio (C#)](../../../../csharp/programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 Pokazuje, jak serializacji może służyć do utrwalenia danych obiektu między wystąpieniami, co umożliwia przechowywanie wartości i pobrać je przy następnym utworzeniu wystąpienia obiektu.  
  
 [Porady: odczytywanie danych o obiektach z pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 Pokazuje, jak można odczytać danych obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
 [Porady: wpisywanie danych o obiektach do pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 Przedstawia sposób zapisania obiektu z klasy do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.
