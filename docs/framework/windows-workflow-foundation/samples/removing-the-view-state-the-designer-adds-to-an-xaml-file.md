---
title: Usuwanie stanu widoku Projektanta dodaje do pliku XAML
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: ed2fda0bb66b2c8fe58c60acc6f80b9e9c8e984e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524955"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Usuwanie stanu widoku Projektanta dodaje do pliku XAML
W tym przykładzie pokazano, jak utworzyć klasę, która jest pochodną <xref:System.Windows.Markup.XamlWriter> i usuwa wyświetlanie stanu z pliku XAML. [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] zapisuje informacje w dokumencie XAML, który jest znany jako stan widoku. Wyświetl stan odnosi się do informacje, które są wymagane w czasie projektowania, takie jak układ pozycjonowanie, i które nie są wymagane w czasie wykonywania. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] Wstawia tych informacji do dokumentu XAML jest edytowany. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] zapisuje stan widoku w pliku XAML z `mc:Ignorable` atrybutu, dzięki czemu te informacje nie został załadowany, gdy środowisko uruchomieniowe ładuje plik XAML. W tym przykładzie pokazano, jak utworzyć klasę, która powoduje usunięcie tego widoku stanu podczas przetwarzania węzłów XAML.  
  
## <a name="discussion"></a>Dyskusja  
 W tym przykładzie pokazano, jak utworzyć niestandardowy Edytor.  
  
 Aby utworzyć niestandardowy Edytor XAML, należy utworzyć klasę, która dziedziczy po elemencie <xref:System.Windows.Markup.XamlWriter>. Autorzy XAML często są zagnieżdżone, jest typowy do śledzenia "wewnętrzny" zapisywania XAML. Te "wewnętrzny" autorzy można traktować jako odwołanie do pozostałych stosu moduły zapisujące XAML, dzięki czemu możesz mieć wiele punktów wejścia do pracy i następnie poprzez delegowanie przekazać przetwarzania do pozostałej części stosu.  
  
 W tym przykładzie istnieje kilka elementów zainteresowania. Jeden jest sprawdzenie, czy element zapisywana jest z projektanta przestrzeni nazw. Należy pamiętać, że to również musiał użycie innych typów z przestrzeni nazw projektanta przepływu pracy.  
  
```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)  
{  
    return xamlMember.IsAttachable &&  
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);  
}  
  
const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";  

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.  
public ViewStateCleaningWriter(XamlWriter innerWriter)  
{  
    this.InnerWriter = innerWriter;  
    this.MemberStack = new Stack<XamlMember>();  
}  
  
XamlWriter InnerWriter {get; set; }  
Stack<XamlMember> MemberStack {get; set; }  
```  
  
 Tworzy to również stosu XAML elementów członkowskich, które są używane podczas rekursywnego przesyłania strumień węzłów. Praca pozostała tego przykładu stopniu znajduje się w <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metody.  
  
```csharp
public override void WriteStartMember(XamlMember xamlMember)  
{  
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))  
    {  
        m_attachedPropertyDepth++;  
    }  
  
    if (m_attachedPropertyDepth > 0)  
    {  
        return;  
    }  
  
    InnerWriter.WriteStartMember(xamlMember);  
}  
```  
  
 Kolejne metody, a następnie sprawdź, czy nadal znajdują się w kontenerze stanu widoku, a jeśli tak, wróć i nie przekazuj węzeł w dół stosu składnika zapisywania.  
  
```csharp
public override void WriteValue(Object value)  
{  
    if (m_attachedPropertyDepth > 0)  
    {  
        return;  
    }  
  
    InnerWriter.WriteValue(value);  
}  
```  
  
 Aby użyć niestandardowego Edytor XAML, możesz musi zostać połączony je ze sobą w stosie autorzy XAML. Poniższy kod pokazuje, jak może być używany.  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ViewStateCleaningWriter.sln.  
  
2. Otwórz wiersz polecenia i przejdź do katalogu, w którym ViewStageCleaningWriter.exe jest wbudowana.  
  
3. Uruchomienie pliku Workflow1.xaml ViewStateCleaningWriter.exe.  

   Składnia dla pliku wykonywalnego jest wyświetlana w poniższym przykładzie.  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   Spowoduje to wygenerowanie pliku XAML do \[outfile], która zawiera wszystkie jej informacje o stanie widoku usunięte.  
  
> [!NOTE]
> Aby uzyskać <xref:System.Activities.Statements.Sequence> przepływu pracy, liczba wirtualizacji wskazówki są usuwane. Powoduje to projektanta Aby ponownie Oblicz układ następnym razem, gdy jest on ładowany. Kiedy korzystać z tej próbki dla <xref:System.Activities.Statements.Flowchart>, pozycjonowanie i wiersza informacji o routingu są usuwane, a w kolejnych ładowanie do projektanta, wszystkie działania są ułożone w lewej części ekranu.  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Aby utworzyć przykładowy plik XAML do użytku z tego przykładu  
  
1. Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2. Utwórz nową aplikację konsoli przepływu pracy.  
  
3. Przeciąganie i upuszczanie kilka działania na kanwę  
  
4. Zapisz plik XAML przepływu pracy.  
  
5. Sprawdź plik XAML, aby wyświetlić widok stanu dołączone właściwości.  
  
> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
