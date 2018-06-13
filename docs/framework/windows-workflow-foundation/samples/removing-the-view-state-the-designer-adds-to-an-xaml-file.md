---
title: Dodaje usuwanie stanu widoku projektanta do pliku XAML
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f63723c29c76854602308ba3e8d7e6dd65d9fb94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517839"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Dodaje usuwanie stanu widoku projektanta do pliku XAML
Ten przykład przedstawia sposób tworzenia klasy pochodnej z <xref:System.Windows.Markup.XamlWriter> i usuwa wyświetlania stanu z pliku XAML. [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] zapisuje informacje do dokumentu XAML, znany jako stan widoku. Stan widoku odwołuje się do informacji, które jest wymagany w czasie projektowania, takie jak układ rozmieszczania, który nie jest wymagany w czasie wykonywania. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] Wstawia te informacje do dokumentu XAML jest edytowany. [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] zapisuje stan widoku w pliku XAML z `mc:Ignorable` atrybutu, dlatego te informacje nie został załadowany, gdy środowisko uruchomieniowe ładuje plik XAML. W tym przykładzie pokazano, jak utworzyć klasę, która usuwa informacje o stanie tego widoku podczas przetwarzania węzłów XAML.  
  
## <a name="discussion"></a>Omówienie  
 Ten przykład przedstawia sposób tworzenia niestandardowego modułu zapisującego.  
  
 Do tworzenia niestandardowych zapisywania XAML, Utwórz klasę, która dziedziczy <xref:System.Windows.Markup.XamlWriter>. Jak często są zagnieżdżone autorów XAML, jest typowe do śledzenia "wewnętrzne" zapisywania XAML. Te "wewnętrzne" zapisywania można traktować jako odwołanie do stosu pozostałych składników zapisywania XAML, co pozwala mieć wiele punktów wejścia do pracy i następnie poprzez delegowanie przekazać przetwarzanie reszta stosu.  
  
 W tym przykładzie istnieje kilka elementy. Jeden jest sprawdzenie, czy element zapisywana jest z projektanta przestrzeni nazw. Należy pamiętać, że to również usuwa użycie innych typów z projektanta przestrzeni nazw w przepływie pracy.  
  
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
  
 Daje to stosu XAML elementów członkowskich, które są używane podczas przechodzenia przez strumień węzłów. Praca pozostała tego przykładu przede wszystkim znajduje się w <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metody.  
  
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
  
 Kolejne metody, a następnie sprawdź, czy nadal znajdują się w kontenerze stan widoku, a jeśli tak, wróć i nie są przekazywane węzeł w dół stosu składnika zapisywania.  
  
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
  
 Aby użyć niestandardowej zapisywania XAML, możesz musi łańcuch go w stosie składników zapisywania XAML. Poniższy kod przedstawia sposób może być używany.  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ViewStateCleaningWriter.sln.  
  
2. Otwórz wiersz polecenia i przejdź do katalogu, w którym ViewStageCleaningWriter.exe jest wbudowana.  
  
3. Uruchom ViewStateCleaningWriter.exe Workflow1.xaml pliku.  

   W poniższym przykładzie przedstawiono składnię pliku wykonywalnego.  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   To generuje plik XAML do \[outfile], która zawiera wszystkie jego Wyświetl informacje o stanie usunięte.  
  
> [!NOTE]
> Aby uzyskać <xref:System.Activities.Statements.Sequence> przepływu pracy, liczba wirtualizacji wskazówki są usuwane. Powoduje to projektanta, aby ponownie Oblicz układ następnym razem, gdy jest ładowany. Jeśli używasz tego przykładu dla <xref:System.Activities.Statements.Flowchart>, pozycjonowanie i linii routingu informacje zostaną usunięte i wszystkie działania w kolejnych ładowania do projektanta, stos po lewej stronie ekranu.  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Aby utworzyć przykładowy plik XAML do użytku z tego przykładu  
  
1. Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2. Utwórz nową aplikację konsoli przepływu pracy.  
  
3. Przeciągnij i upuść kilka działań na kanwę  
  
4. Zapisz plik XAML przepływu pracy.  
  
5. Sprawdź plik XAML, aby wyświetlić widok stanu dołączone właściwości.  
  
> [!IMPORTANT]
> Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
