---
title: Narzędzie Contract-First
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: ad0566eaff08d27e8368f091388adda7376a37ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608647"
---
# <a name="contract-first-tool"></a>Narzędzie Contract-First
Kontrakty usług często muszą zostać utworzone z istniejącymi usługami. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], klasy kontraktu danych mogą być tworzone automatycznie z istniejącymi usługami za pomocą narzędzie contract-first. Aby użyć narzędzie contract-first, plik definicji schematu XML (XSD), należy pobrać lokalnie; Narzędzie nie może zaimportować kontraktów danych zdalnych za pośrednictwem protokołu HTTP.

 Narzędzie contract-first jest zintegrowana w Visual Studio 2012 jako zadanie kompilacji. Kod generowany przez zadanie kompilacji tworzonych każdym razem, gdy projekt jest kompilowany, tak, aby projekt łatwo można przyjąć zmiany podstawowego kontraktu usługi.

 Następujące typy schematu, które można importować narzędzie contract-first:

```xml
<xsd:complexType>
<xsd:simpleType>
```

 Proste typy nie zostanie wygenerowany, jeśli są w nim elementów podstawowych takich jak `Int16` lub `String`; złożonych typów nie zostanie wygenerowany, jeśli są one typu `Collection`. Typy również nie zostanie wygenerowany, jeśli są one częścią innego `xsd:complexType`. W takich przypadkach typy będzie odwoływać się do istniejących typów w projekcie zamiast tego.

## <a name="adding-a-data-contract-to-a-project"></a>Dodawanie kontraktu danych do projektu
 Narzędzie contract-first mogą być używane, kontrakt usługi (XSD) należy dodać do projektu. Na potrzeby tego omówienia następujących kontraktu będzie służyć do zilustrowania funkcje wymogiem wcześniejszego zawarcia kontraktu. Definicja ta usługa jest mały podzbiór kontraktu usługi używane przez interfejs API wyszukiwania Bing.

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

 Aby dodać powyżej kontraktu usługi do projektu, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj nowy...** . Wybierz definicję schematu z poziomu okienka WCF okna dialogowego szablony i nadaj nowemu plikowi SampleContract.xsd. Skopiuj i Wklej powyższy kod do widoku kodu, nowego pliku.

## <a name="configuring-contract-first-options"></a>Konfigurowanie opcji wymogiem wcześniejszego zawarcia kontraktu
 W menu Właściwości projektu programu WCF można skonfigurować opcje wymogiem wcześniejszego zawarcia kontraktu. Aby włączyć programowania z wymogiem wcześniejszego zawarcia kontraktu, zaznacz **Włącz XSD jako język definicji typu** pole wyboru na stronie usługi WCF w oknie właściwości projektu.

 ![Zrzut ekranu przedstawiający opcje WCF za pomocą programowania z wymogiem wcześniejszego zawarcia kontraktu włączone.](./media/contract-first-tool/contract-first-options.png)

 Aby skonfigurować zaawansowane właściwości, kliknij przycisk Zaawansowane.

 ![Okno dialogowe Zaawansowane ustawienia generowania kodu kontraktu.](./media/contract-first-tool/advanced-contract-settings.png)

 Można skonfigurować następujące ustawienia zaawansowane dla generowania kodu z umów. Ustawienia można skonfigurować tylko dla wszystkich plików w projekcie; ustawienia nie można skonfigurować dla poszczególnych plików w tej chwili.

- **Tryb serializator**: To ustawienie określa, które serializator służy do odczytywania plików kontraktu usługi. Gdy **serializatora XML** jest zaznaczone, **typy kolekcji** i **Użyj ponownie typów** opcje zostaną wyłączone. Te opcje mają zastosowanie tylko do **serializator kontraktu danych**.

- **Ponownie użyj typów**: To ustawienie określa, które biblioteki są używane do ponownego użycia typu. To ustawienie dotyczy tylko, jeśli **tryb serializator** ustawiono **serializator kontraktu danych**.

- **Typ kolekcji**: To ustawienie określa w pełni kwalifikowaną lub kwalifikowaną dla zestawu typu ma być używany dla typu danych kolekcji. To ustawienie dotyczy tylko, jeśli **tryb serializator** ustawiono **serializator kontraktu danych**.

- **Typ słownika**: To ustawienie określa w pełni kwalifikowaną lub kwalifikowaną dla zestawu typu ma być używany dla typu danych słownika.

- **EnableDataBinding**: To ustawienie określa, czy wdrożyć <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu dla wszystkich typów danych do zaimplementowania powiązanie danych.

- **Elementu ExcludedTypes**: to ustawienie określa listę w pełni kwalifikowaną lub kwalifikowaną dla zestawu typów, które mają być wykluczone z przywoływanych zestawów. To ustawienie dotyczy tylko, jeśli **tryb serializator** ustawiono **serializator kontraktu danych**.

- **GenerateInternalTypes**: To ustawienie określa, czy mają zostać wygenerowane klasy, które są oznaczone jako wewnętrzne. To ustawienie dotyczy tylko, jeśli **tryb serializator** ustawiono **serializator kontraktu danych**.

- **GenerateSerializableTypes**: To ustawienie określa, czy mają zostać wygenerowane klasy z <xref:System.SerializableAttribute> atrybutu. To ustawienie dotyczy tylko, jeśli **tryb serializator** ustawiono **serializator kontraktu danych**.

- **ImportXMLTypes**: To ustawienie określa, czy ma być konfigurowane serializator kontraktu danych, aby zastosować <xref:System.SerializableAttribute> atrybutów do klasy bez <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu.  To ustawienie dotyczy tylko, jeśli **tryb serializator** ustawiono **serializator kontraktu danych**.

- **SupportFx35TypedDataSets**: To ustawienie określa, czy oferowanie dodatkowych funkcji dla typizowanych zestawów danych utworzonych dla .NET Framework 3.5. Gdy **tryb serializator** jest ustawiona na **serializatora XML**, <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> rozszerzenia zostaną dodane do importera schematów XML, gdy ta wartość jest ustawiona na wartość True. Gdy **tryb serializator** jest ustawiona na **serializator kontraktu danych**, typ <xref:System.DateTimeOffset> zostaną wykluczone z odwołań, gdy ta wartość jest ustawiona na wartość False, tak, aby <xref:System.DateTimeOffset> był zawsze generowany w przypadku starszych wersji framework.

- **InputXsdFiles**: To ustawienie określa listę plików wejściowych. Każdy plik musi zawierać prawidłowy schemat XML.

- **Język**: To ustawienie określa język generowanego kodu kontraktu. Ustawienie musi być rozpoznawalna przy <xref:System.CodeDom.Compiler.CodeDomProvider>.

- **NamespaceMappings**: To ustawienie określa mapowania z docelowych przestrzeni nazw XSD do przestrzeni nazw CLR. Każdego mapowania należy użyć następującego formatu:

    ```xml
    "<Schema Namespace>, <CLR Namespace>"
    ```

     Szeregujący XML akceptuje tylko jedno mapowanie w następującym formacie:

    ```xml
    "*, <CLR Namespace>"
    ```

- **OutputDirectory**: To ustawienie określa katalog, w którym zostaną wygenerowane pliki kodu.

 Ustawienia będzie służyć do generowania typów kontraktu usługi z plików kontraktu usługi, gdy projekt jest kompilowany.

## <a name="using-contract-first-development"></a>Za pomocą programowania z wymogiem wcześniejszego zawarcia kontraktu
 Po Dodawanie kontraktu usługi do projektu i Potwierdzanie ustawień kompilacji, skompiluj projekt, naciskając klawisz **F6**. Typy zdefiniowane w kontrakcie usługi będzie dostępny do użytku w projekcie.

 Aby użyć typów zdefiniowanych w kontrakcie usługi, należy dodać odwołanie do `ContractTypes` w bieżącej przestrzeni nazw:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Typy zdefiniowane w kontrakcie usługi będzie rozpoznawany w projekcie, jak pokazano poniżej:

 ![Klasa SearchRequest wyświetlanie w IntelliSense po wpisaniu kilka pierwszych liter.](./media/contract-first-tool/service-contract-types.png)

 Typy generowane przez narzędzie są tworzone w pliku GeneratedXSDTypes.cs. Plik jest tworzony w \<katalogu projektu > /obj/\<Konfiguracja kompilacji > katalog /XSDGeneratedCode/ domyślnie. Schemat przykładowych na początku tego tematu jest konwertowany w następujący sposób:

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
 Podczas kompilacji, błędy i ostrzeżenia, błędy i ostrzeżenia podczas analizowania schematu XSD będą wyświetlane.

## <a name="interface-inheritance"></a>Dziedziczenia interfejsu
 Nie jest możliwe użycie dziedziczenia interfejsu z wymogiem wcześniejszego zawarcia kontraktu rozwoju. jest to zgodne ze sposobem, w jaki interfejsów zachowują się w innych operacji. Aby można było używać interfejsu dziedzicząca interfejs podstawowy, użyj dwa oddzielne punkty końcowe. Pierwszy punkt końcowy korzysta z dziedziczonych kontraktu, a drugiego punktu końcowego implementuje interfejs podstawowy.
