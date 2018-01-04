---
title: "Narzędzie Contract-First"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5079a4b45c7adf0cfd4d9ae1069379184422dc98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="contract-first-tool"></a>Narzędzie Contract-First
Kontrakty usług często muszą być utworzone na podstawie istniejących usług. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], klasy kontraktu danych mogą być tworzone automatycznie z istniejącymi usługami za pomocą narzędzie contract-first. Aby użyć narzędzie contract-first, plik definicji schematu XML (XSD), należy pobrać lokalnie; Narzędzie nie może zaimportować kontraktów danych zdalnych za pośrednictwem protokołu HTTP.  
  
 Narzędzie contract-first jest zintegrowany z [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] jako zadania kompilacji. Pliki kod wygenerowany przez zadanie kompilacji są tworzone co projekt jest budowany, dzięki czemu projektu można łatwo przyjęcia zmian w podstawowej kontraktu usługi.  
  
 Typów schematów, które można importować narzędzie contract-first są następujące:  
  
```xml  
<xsd:complexType>  
<xsd:simpleType>  
```  
  
 Proste typy nie zostanie wygenerowany, jeśli są w nim elementów podstawowych takich jak `Int16` lub `String`; złożonych typów nie zostanie wygenerowany, jeśli są one typu `Collection`. Typy również nie zostanie wygenerowany, jeśli są one częścią innego `xsd:complexType`. W takich przypadkach typy będzie odwoływać się do istniejących typów w projekcie zamiast tego.  
  
## <a name="adding-a-data-contract-to-a-project"></a>Dodawanie kontraktu danych do projektu  
 Przed użyciem narzędzie contract-first kontraktu usługi (XSD) należy dodać do projektu. Na potrzeby ten przegląd następujące kontraktu będzie służyć do zilustrowanie funkcji pierwszy kontraktu. Ta definicja usługi jest mały podzbiór kontraktu usługi używane przez funkcję wyszukiwania usługi Bing dla interfejsu API.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="ServiceSchema"  
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"  
    elementFormDefault="qualified"  
    xmlns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"  
>  
  <xs:complexType name="SearchRequest">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:simpleType name="WebSearchOption">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="DisableHostCollapsing" />  
      <xs:enumeration value="DisableQueryAlterations" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
 Aby dodać powyżej kontraktu usługi do projektu, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj nowy...** . Wybierz definicję schematu z okienka WCF okna dialogowego szablony, a nazwa nowego pliku SampleContract.xsd. Skopiuj i Wklej powyższy kod do widoku kodu nowego pliku.  
  
## <a name="configuring-contract-first-options"></a>Konfigurowanie opcji pierwszy kontraktu  
 W menu właściwości można skonfigurować opcje kontraktu pierwszy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu. Aby umożliwić programowanie pierwszy kontraktu, zaznacz **włączyć XSD jako język definicji typu** pole wyboru na stronie WCF w oknie właściwości projektu.  
  
 ![Opcje projektu WCF przedstawiający kontraktu &#45; pierwszej](../../../docs/framework/wcf/media/contractfirstoptions.png "ContractFirstOptions")  
  
 Aby skonfigurować zaawansowane właściwości, kliknij przycisk Zaawansowane.  
  
 ![Zaawansowane kontraktu &#45; Pierwszy właściwości](../../../docs/framework/wcf/media/contractfirstadvanced.png "ContractFirstAdvanced")  
  
 Można skonfigurować następujące ustawienia zaawansowane dla generowanie kodu na podstawie umów. Ustawienia można skonfigurować tylko dla wszystkich plików w projekcie; Nie można skonfigurować ustawień dla poszczególnych plików w tej chwili.  
  
-   **Tryb serializator**: to ustawienie określa, które serializator służy do odczytywania plików kontraktu usługi. Gdy **serializatora XML** jest zaznaczone, **typy kolekcji** i **ponowne użycie typów** opcje zostaną wyłączone. Ta opcja ma zastosowanie tylko do **serializator kontraktu danych**.  
  
-   **Ponownie użyj typów**: to ustawienie określa, które biblioteki są używane do ponownego użycia typu. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializator** ustawiono **serializator kontraktu danych**.  
  
-   **Typ kolekcji**: to ustawienie określa typ pełni kwalifikowaną lub kwalifikowaną dla zestawu do zastosowania w przypadku typu danych kolekcji. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializator** ustawiono **serializator kontraktu danych**.  
  
-   **Typ słownikowy**: to ustawienie określa typ pełni kwalifikowaną lub kwalifikowaną dla zestawu do użycia dla typu danych słownika.  
  
-   **EnableDataBinding**: to ustawienie określa, czy wdrożyć <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu na wszystkich typach danych do zaimplementowania wiązania z danymi.  
  
-   **ExcludedTypes**: to ustawienie określa listę w pełni kwalifikowaną lub kwalifikowaną dla zestawu typów, które mają być wykluczone z przywoływanych zestawach. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializator** ustawiono **serializator kontraktu danych**.  
  
-   **GenerateInternalTypes**: to ustawienie określa, czy mają zostać wygenerowane klasy, które są oznaczone jako wewnętrzne. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializator** ustawiono **serializator kontraktu danych**.  
  
-   **GenerateSerializableTypes**: to ustawienie określa, czy można wygenerować klas z <xref:System.SerializableAttribute> atrybutu. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializator** ustawiono **serializator kontraktu danych**.  
  
-   **ImportXMLTypes**: to ustawienie określa, czy do konfigurowania serializator kontraktu danych, aby zastosować <xref:System.SerializableAttribute> atrybutu klasy bez <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu.  To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializator** ustawiono **serializator kontraktu danych**.  
  
-   **SupportFx35TypedDataSets**: to ustawienie określa, czy oferowanie dodatkowych funkcji typizowanych zbiorów danych utworzone dla programu .net Framework 3.5. Gdy **tryb serializator** ustawiono **serializatora XML**, <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> rozszerzenie zostanie dodany do importera schematów XML, gdy ta wartość jest równa True. Gdy **tryb serializator** ma ustawioną wartość **serializator kontraktu danych**, typ <xref:System.DateTimeOffset> zostaną wykluczone z odwołań, gdy ta wartość jest równa False, aby <xref:System.DateTimeOffset> był zawsze generowany dla starszych wersji framework.  
  
-   **InputXsdFiles**: to ustawienie określa listę plików wejściowych. Każdy plik musi zawierać prawidłowy schematu XML.  
  
-   **Język**: to ustawienie określa język generowanego kodu kontraktu. Ustawienie musi być rozpoznawalna przy <xref:System.CodeDom.Compiler.CodeDomProvider>.  
  
-   **NamespaceMappings**: to ustawienie określa mapowania z docelowej przestrzeni nazw XSD do przestrzeni nazw CLR. Każdego mapowania należy użyć następującego formatu:  
  
    ```xml  
    "<Schema Namespace>, <CLR Namespace>"  
    ```  
  
     Szeregujący XML akceptuje tylko jedno mapowanie w następującym formacie:  
  
    ```xml  
    "*, <CLR Namespace>"  
    ```  
  
-   **OutputDirectory**: to ustawienie określa katalog, w której zostanie wygenerowane plików kodu.  
  
 Ustawienia będą używane do generowania typów kontraktu usługi z plików kontraktu usługi, gdy projekt jest budowany.  
  
## <a name="using-contract-first-development"></a>Przy użyciu pierwszej kontraktu programowanie  
 Po Dodawanie kontraktu usługi do projektu i potwierdzenie ustawień kompilacji kompilacji projektu przez naciśnięcie przycisku **F6**. Typy zdefiniowane w kontrakcie usługi będzie dostępna do użycia w projekcie.  
  
 Aby korzystać z typów definiowanych w kontrakcie usługi, dodać odwołanie do `ContractTypes` w bieżącej przestrzeni nazw:  
  
```csharp  
using MyProjectNamespace.ContractTypes;  
```  
  
 Typy zdefiniowane w kontrakcie usługi będzie rozpoznawany w projekcie, jak pokazano poniżej.  
  
 ![Używanie typów pochodnych kontrakt usługi](../../../docs/framework/wcf/media/contractfirsttypes.png "ContractFirstTypes")  
  
 Typy generowane przez narzędzie są tworzone w pliku GeneratedXSDTypes.cs. Plik jest tworzony w \<katalogu projektu > /obj/\<przy tworzeniu konfiguracji > katalogu /XSDGeneratedCode/ domyślnie. Schemat przykładowe na początku tego tematu jest konwertowane w następujący sposób:  
  
```csharp
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:4.0.30319.17330  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace TestXSD3.ContractTypes  
{  
    using System.Xml.Serialization;  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.ComponentModel.DesignerCategoryAttribute("code")]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]  
    public partial class SearchRequest  
    {  
  
        private string versionField;  
  
        private string marketField;  
  
        private string uILanguageField;  
  
        private string queryField;  
  
        private string appIdField;  
  
        private double latitudeField;  
  
        private bool latitudeFieldSpecified;  
  
        private double longitudeField;  
  
        private bool longitudeFieldSpecified;  
  
        private double radiusField;  
  
        private bool radiusFieldSpecified;  
  
        public SearchRequest()  
        {  
            this.versionField = "2.2";  
        }  
  
        /// <remarks/>  
        [System.ComponentModel.DefaultValueAttribute("2.2")]  
        public string Version  
        {  
            get  
            {  
                return this.versionField;  
            }  
            set  
            {  
                this.versionField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Market  
        {  
            get  
            {  
                return this.marketField;  
            }  
            set  
            {  
                this.marketField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string UILanguage  
        {  
            get  
            {  
                return this.uILanguageField;  
            }  
            set  
            {  
                this.uILanguageField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Query  
        {  
            get  
            {  
                return this.queryField;  
            }  
            set  
            {  
                this.queryField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string AppId  
        {  
            get  
            {  
                return this.appIdField;  
            }  
            set  
            {  
                this.appIdField = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Latitude  
        {  
            get  
            {  
                return this.latitudeField;  
            }  
            set  
            {  
                this.latitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LatitudeSpecified  
        {  
            get  
            {  
                return this.latitudeFieldSpecified;  
            }  
            set  
            {  
                this.latitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Longitude  
        {  
            get  
            {  
                return this.longitudeField;  
            }  
            set  
            {  
                this.longitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LongitudeSpecified  
        {  
            get  
            {  
                return this.longitudeFieldSpecified;  
            }  
            set  
            {  
                this.longitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Radius  
        {  
            get  
            {  
                return this.radiusField;  
            }  
            set  
            {  
                this.radiusField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool RadiusSpecified  
        {  
            get  
            {  
                return this.radiusFieldSpecified;  
            }  
            set  
            {  
                this.radiusFieldSpecified = value;  
            }  
        }  
    }  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]  
    public enum WebSearchOption  
    {  
  
        /// <remarks/>  
        DisableHostCollapsing,  
  
        /// <remarks/>  
        DisableQueryAlterations,  
    }  
}  
```  
  
## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia  
 Podczas tworzenia błędy i ostrzeżenia będą wyświetlane błędy i ostrzeżenia podczas analizowania schematu XSD.  
  
## <a name="interface-inheritance"></a>Dziedziczenie — interfejs  
 Nie można użyć interfejsu dziedziczenia z pierwszej kontraktu rozwoju; jest to zgodne ze sposobem, w jaki interfejsy się odbywać na innych operacji. Aby można było używać interfejsu, który dziedziczy interfejs podstawowy, użyj dwa oddzielne punkty końcowe. Pierwszym punktem końcowym używa dziedziczone kontraktu i drugiego punktu końcowego implementuje interfejs podstawowy.
