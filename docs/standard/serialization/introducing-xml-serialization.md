---
title: Wprowadzenie do serializacji XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, about XML serialization
- ICollection interface, serializing
- XmlSerializer class, serializing
- serialization, about serialization
- DataSet class, serializing
- XML Schema, serializing
ms.assetid: 8c63200d-db63-4a03-a93d-21641623df62
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 13afeecc979cab9719ffa063f78ff91c866262d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="introducing-xml-serialization"></a>Wprowadzenie do serializacji XML
Serializacji to proces konwersji obiektu do formularza, który można łatwo przesłać. Na przykład można serializować obiektu i przetransportować go przez Internet między klientem serwerem przy użyciu protokołu HTTP. Z drugiej deserializacji rekonstruuje obiektów ze strumienia.  
  
 Wykonuje serializacji XML serializację tylko publiczny pól i wartości właściwości obiektu do strumienia XML. Serializacji XML nie zawiera informacji o typie. Na przykład, jeśli masz **książki** obiektu, który istnieje w **biblioteki** przestrzeni nazw, nie ma żadnej gwarancji jest przeprowadzić deserializacji do obiektu tego samego typu.  
  
> [!NOTE]
>  Serializacji XML nie konwertuje metody, indeksatory, prywatnych pola lub właściwości tylko do odczytu (z wyjątkiem kolekcji tylko do odczytu). Do serializacji obiektu wszystkie pola i właściwości, zarówno publiczne, jak i prywatnych, użyj <xref:System.Runtime.Serialization.DataContractSerializer> zamiast serializacji XML.  
  
 Klasa centralnej w serializacji XML jest <xref:System.Xml.Serialization.XmlSerializer> klasy i najważniejsze metody tej klasy są **serializacja** i **Deserialize** metody. <xref:System.Xml.Serialization.XmlSerializer> Tworzy PLiki C# i kompiluje je na PLiki z rozszerzeniem dll do wykonania tej serializacji. W programie .NET Framework 2.0 [narzędzie generowania serializatora XML (Sgen.exe)](../../../docs/standard/serialization/xml-serializer-generator-tool-sgen-exe.md) jest przeznaczona do generowania tych zestawów serializacji wcześniej do wdrożenia razem z aplikacji i zwiększyć wydajność uruchamiania. Strumień XML wygenerowanych przez **XmlSerializer** jest zgodne z konsorcjum World Wide Web (www.w3.org) języka definicji schematu XML (XSD) 1.0 zalecenia. Ponadto wygenerowane typy danych są zgodne z dokumentem zatytułowany "część schematu XML 2: typy danych."  
  
 Dane w obiektów opisano przy użyciu narzędzi programistycznych języka, takich jak klasy, pola, właściwości, typy pierwotne, tablic i nawet osadzonych XML w formie **XmlElement** lub **XmlAttribute**obiektów. Istnieje możliwość tworzenia własnych klas oznaczona z atrybutów, lub za pomocą narzędzia definicji schematu XML można wygenerować klas na podstawie istniejącego schematu XML.  
  
 Jeśli masz schematu XML, należy uruchomić narzędzie definicji schematu XML do tworzenia zestaw klasy, które są silnie wpisany schematu i dodawać adnotacje z atrybutami. W przypadku wystąpienia takich klasy jest serializowana, wygenerowany kod XML jest zgodna schematu XML. Zamieszczone w przypadku klasy, można programować względem model obiektów łatwo manipulować spełniającą pewność, że wygenerowany kod XML jest zgodny ze schematem XML. Jest to alternatywa dla użycia innych klas w programie .NET Framework, takich jak **XmlReader** i **XmlWriter** klas, aby przeanalizować i zapisu to strumień XML. Aby uzyskać więcej informacji, zobacz [dokumenty XML i dane](../../../docs/standard/data/xml/index.md). Klasy te umożliwiają przeanalizować strumieniem XML. Z kolei, użyj **XmlSerializer** kiedy strumień XML jest oczekiwany, aby były zgodne ze znanym schematu XML.  
  
 Atrybuty kontrolować strumień XML wygenerowanych przez **XmlSerializer** klasy, dzięki czemu można ustawić przestrzeni nazw XML, nazwa elementu, nazwa atrybutu i tak dalej, strumienia XML. Aby uzyskać więcej informacji o tych atrybutów i sposób ich kontroli serializacji XML, zobacz [kontrolowanie atrybutów za pomocą serializacji XML](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md). Dla tabeli tych atrybutów, które są używane do kontrolowania wygenerowany kod XML, zobacz [atrybuty który kontroli serializacji XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).  
  
 **XmlSerializer** klasy pozwala dodatkowo szeregowania obiektu i Generuj zakodowany strumień XML protokołu SOAP. Wygenerowany kod XML zgodnego ze sekcji 5 dokumentu sieci World Wide Web konsorcjum "Simple Object Access Protocol (SOAP) 1.1." Aby uzyskać więcej informacji o tym procesie, zobacz [porady: szeregowania obiektu jako strumień XML SOAP-Encoded](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Dla tabeli atrybutów kontrolujących wygenerowany kod XML, zobacz [atrybuty który kontroli zakodowane SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 **XmlSerializer** klasy generuje wiadomości SOAP utworzony przez i przekazany do usług XML sieci Web. Aby kontrolować wiadomości SOAP, można zastosować atrybutów do klasy, zwracanych wartości, parametry i pola znaleziono w pliku usługi XML sieci Web (.asmx). Można użyć atrybuty wymienione w "Serializacji XML atrybuty czy kontroli" i "Atrybuty czy kontroli kodowany protokołu SOAP serializacji", ponieważ usługi XML sieci Web mogą korzystać styl literału lub zakodowanego protokołu SOAP. Aby uzyskać więcej informacji na temat kontrolowania XML wygenerowanych przez usługi XML sieci Web za pomocą atrybutów, zobacz [szeregowanie XML z usług XML sieci Web](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md). Aby uzyskać więcej informacji na temat usług XML sieci Web i SOAP, zobacz [Dostosowywanie wiadomości SOAP](https://msdn.microsoft.com/en-us/subscriptions/index/dkwy2d72\(v=vs.71\).aspx).  
  
## <a name="security-considerations-for-xmlserializer-applications"></a>Zagadnienia dotyczące zabezpieczeń dla aplikacji XmlSerializer  
 Podczas tworzenia aplikacji, która używa **XmlSerializer**, należy zwrócić uwagę na następujące elementy i ich wpływ na:  
  
-   **XmlSerializer** tworzy C# (CS), pliki i kompiluje je do plików dll w katalogu o nazwie przez zmienną środowiskową TEMP; serializacji występuje z tych bibliotek DLL.  
  
    > [!NOTE]
    >  Te zestawy serializacji można wygenerowane z góry i podpisane za pomocą narzędzia SGen.exe. Nie działa serwer usług sieci Web. Innymi słowy jest tylko do użytku klienta i ręczne serializacji.  
  
     Kod i biblioteki DLL są podatne na złośliwego procesu w czasie tworzenia i kompilacji. Podczas używania na komputerze z systemem Microsoft Windows NT 4.0 lub nowszy, może być możliwe dla co najmniej dwa użytkownikom udostępnianie katalogu TEMP. Udostępnianie katalogu TEMP jest niebezpieczne, jeśli dwa konta mają uprawnienia zabezpieczeń i konta wyższych uprawnień uruchamia aplikację przy użyciu **XmlSerializer**. W takim przypadku jeden użytkownik może naruszenia zabezpieczeń komputera przez zastąpienie pliku .cs lub dll, który ma być kompilowana. Aby usunąć ten problem, zawsze upewnij się, że każde konto na komputerze ma własny profil. Domyślnie zmienna środowiskowa TEMP wskazuje inny folder dla każdego konta.  
  
-   Jeśli złośliwy użytkownik wysyła stały strumień danych XML do serwera sieci Web (odmowa usługi), a następnie **XmlSerializer** przetwarzania danych, aż komputer ma za mało zasobów w dalszym ciągu.  
  
     Ten rodzaj ataku jest usunięte, jeśli używasz komputer z systemem Internet Information Services (IIS), a aplikacja jest uruchomiona w ramach usług IIS. Program IIS zawiera bramę, która nie może przetwarzać strumieni dłużej niż pewną liczbę (wartość domyślna to 4 KB). Jeśli tworzenie aplikacji, która nie korzysta z usług IIS i deserializuje z **XmlSerializer**, należy zaimplementować podobne bramy, który uniemożliwia typu "odmowa usługi".  
  
-   **XmlSerializer** serializuje dane i uruchamia kod za pomocą dowolnego typu nadane.  
  
     Istnieją dwie metody, w których obiekt złośliwego przedstawia zagrożenia. Można uruchomić złośliwego kodu lub jego można wstawić złośliwy kod do pliku C# utworzone przez **XmlSerializer**. W przypadku pierwszego Jeśli obiekt złośliwego próbuje uruchomić destrukcyjne procedurę, zabezpieczenia dostępu do kodu uniemożliwia szkody wykonywana. W drugim przypadku jest teoretyczna możliwość, że złośliwe obiektu może jakiś sposób iniekcję kodu do pliku C# utworzonego przez **XmlSerializer**. Mimo że ten problem zbadaniu dokładnie i takiego ataku jest uznawany za mało prawdopodobne, należy podjąć środki ostrożności nigdy nie szeregowania danych o typie nieznany i niezaufane.  
  
-   Zserializowany poufnych danych może być narażony.  
  
     Po **XmlSerializer**zawiera seryjnych danych, mogą być przechowywane jako plik XML lub innym magazynie danych. Sklepu danych jest dostępna dla innych procesów, czy jest widoczny w intranecie lub w Internecie, dane mogą skradziony i użyty w sposób złośliwy. Na przykład, jeśli tworzysz aplikację serializujący zamówień zawierające numery kart kredytowych, dane są bardzo ważne. Aby zapobiec, zawsze ochrony magazynu danych i wykonać kroki, aby utrzymać ją prywatnych.  
  
## <a name="serialization-of-a-simple-class"></a>Serializacja prostą klasę  
 Poniższy przykładowy kod przedstawia podstawowe klasy z publicznym polem.  
  
```vb  
Public Class OrderForm  
    Public OrderDate As DateTime  
End Class  
```  
  
```csharp  
public class OrderForm  
{  
    public DateTime OrderDate;  
}  
```  
  
 W przypadku wystąpienia tej klasy jest serializowana, jego może wyglądać w następujący sposób.  
  
```xml  
<OrderForm>  
    <OrderDate>12/12/01</OrderDate>  
</OrderForm>  
```  
  
 Aby uzyskać więcej przykładów serializacji, zobacz [przykłady serializacji XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
## <a name="items-that-can-be-serialized"></a>Elementy, które można wykonywać serializację  
 Następujące elementy można zserializować przy użyciu **XmLSerializer** klasy:  
  
-   Właściwości publiczne odczytu/zapisu i pola publiczne klas.  
  
-   Klasy, które implementują **ICollection** lub **IEnumerable**.  
  
    > [!NOTE]
    >  Tylko kolekcje są serializacji, nie publiczny właściwości.  
  
-   **Element XmlElement** obiektów.  
  
-   **Element XmlNode** obiektów.  
  
-   **Zestaw danych** obiektów.  
  
 Aby uzyskać więcej informacji na temat serializacji lub deserializacji obiektów, zobacz [porady: szeregowania obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md) i [porady: deserializacji obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md).  
  
## <a name="advantages-of-using-xml-serialization"></a>Korzyści wynikające z używania serializacji XML  
 **XmlSerializer**klasy daje pełny i elastyczną kontrolę podczas szeregowania obiektu jako XML. W przypadku tworzenia usługi XML sieci Web, można zastosować atrybutów, które sterowania serializacją do klas i członków, aby upewnić się, że dane wyjściowe XML jest zgodny z określonym schematem.  
  
 Na przykład **XmlSerializer** umożliwia:  
  
-   Określ, czy pole lub właściwość powinien być kodowany jako atrybut lub element.  
  
-   Określ przestrzeni nazw XML do użycia.  
  
-   Określ nazwę elementu lub atrybutu, jeśli nazwa pola lub właściwości jest nieodpowiedni.  
  
 Inną zaletą serializacji XML jest nie ograniczenia dotyczące aplikacji, które tworzysz, dopóki strumień XML, który jest generowany odpowiada danym schematu. Wyobraź sobie schematu, używany do opisania książki. Zawiera funkcje tytuł, autor, Wydawca i ISBN numer elementu. Możesz utworzyć aplikację, która przetwarza dane XML w dowolny sposób ma, na przykład jako kolejność książki lub spis książek. W obu przypadkach jedynym wymaganiem jest, czy strumień XML jest zgodny ze schematem określonego języka (XSD) definicji schematu XML.  
  
## <a name="xml-serialization-considerations"></a>Uwagi dotyczące serializacji XML  
 Następujące należy uwzględnić podczas przy użyciu **XmlSerializer** klasy:  
  
-   Narzędzie Sgen.exe wyraźnie jest przeznaczona do generowania zestawów serializacji w celu uzyskania optymalnej wydajności.  
  
-   Serializowane dane zawiera tylko danych i struktury klas. Informacje o tożsamości i zestawu typu nie są uwzględniane.  
  
-   Może być Zserializowany tylko właściwości publiczne i pola. Właściwości muszą mieć publiczne metody dostępu (Pobieranie i ustawianie metody). Jeśli muszą serializację danych bez publicznego, użyj <xref:System.Runtime.Serialization.DataContractSerializer> klasy zamiast serializacji XML.  
  
-   Klasa musi mieć konstruktora domyślnego przez **XmlSerializer**.  
  
-   Nie można serializować metody.  
  
-   **Element XmlSerializer** może przetwarzać klas implementujących **IEnumerable** lub **ICollection** inaczej, jeśli spełniają określone wymagania w następujący sposób.  
  
     Klasa, która implementuje **IEnumerable** musi implementować publiczny **Dodaj** metodę, która przyjmuje jeden parametr. **Dodaj** parametru metody muszą być zgodne z typem zwracanym od (polimorficznym) **właściwości IEnumerator.Current** właściwości zwróconej z **GetEnumerator** Metoda.  
  
     Klasa, która implementuje **ICollection** oprócz **IEnumerable** (takich jak **CollectionBase**) musi mieć publiczny **elementu** indeksowane liczb całkowitych i jego właściwości (indeksator w języku C#) musi mieć publiczny **liczba** właściwości typu **całkowitą**. Parametr przekazany do **Dodaj** metoda musi być taki sam typ jak zwrócona **elementu** właściwości lub jednego z typów podstawowych tego typu.  
  
     Dla klas które implementują **ICollection**, są pobierane wartości, aby można było serializować z indeksowanej **elementu** właściwości, a nie przez wywołanie metody **GetEnumerator**. Ponadto publiczne pola i właściwości nie są serializowane, z wyjątkiem pola publiczne, które zwracają innej klasy kolekcji (jeden, który implementuje **ICollection**). Na przykład zobacz [przykłady serializacji XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
## <a name="xsd-data-type-mapping"></a>Mapowania typów danych XSD  
 Dokument konsorcjum World Wide Web (www.w3.org) zatytułowany "XML schematu część 2: typy danych" Określa typy proste danych, które są dozwolone w schemacie schematu XML definition language (XSD). Dla wielu z tych (na przykład **int** i **dziesiętną**), jest odpowiedni typ danych w programie .NET Framework. Jednak niektóre typy danych XML bez odpowiadającego typu danych w programie .NET Framework (na przykład **NMTOKEN** typu danych). W takich przypadkach, jeśli jest używane narzędzie definicji schematu XML ([narzędzie definicji schematu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) można wygenerować klas z schematu, odpowiedni atrybut jest stosowany do elementu członkowskiego typu String i jego **typudanych** właściwość jest ustawiona na nazwę typu danych XML. Na przykład, jeśli schemat zawiera element o nazwie "MyToken" o typie danych XML **NMTOKEN**, wygenerowana klasa może zawierać członka, jak pokazano w poniższym przykładzie.  
  
```vb  
<XmlElement(DataType:="NMTOKEN")> _  
Public MyToken As String  
```  
  
```csharp  
[XmlElement(DataType = "NMTOKEN")]  
public string MyToken;  
```  
  
 Podobnie w przypadku tworzenia klasy, która musi być zgodna do określonego schematu XML (XSD), należy zastosować odpowiedni atrybut i ustawić jej **DataType** nazwa właściwości do żądanych danych XML.  
  
 Pełną listę mapowań typu, zobacz **DataType** właściwości dla każdego z następujących klas atrybutów:  
  
-   <xref:System.Xml.Serialization.SoapAttributeAttribute>  
  
-   <xref:System.Xml.Serialization.SoapElementAttribute>  
  
-   <xref:System.Xml.Serialization.XmlArrayItemAttribute>  
  
-   <xref:System.Xml.Serialization.XmlAttributeAttribute>  
  
-   <xref:System.Xml.Serialization.XmlElementAttribute>  
  
-   <xref:System.Xml.Serialization.XmlRootAttribute>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.IO.FileStream>  
 [XML i serializacji SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Serializacja binarna](../../../docs/standard/serialization/binary-serialization.md)  
 [Serializacja](../../../docs/standard/serialization/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Przykłady serializacji XML](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 [Porady: szeregowania obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Porady: deserializacji obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
