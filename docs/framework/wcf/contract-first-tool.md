---
title: Narzędzie Contract-First
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 36e1a3e19f802ca5b74cf50f5bcd57c167e31e33
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291704"
---
# <a name="contract-first-tool"></a>Narzędzie Contract-First
Umowy serwisowe często muszą być tworzone z istniejących usług. W .NET Framework 4.5 i nowszych klasy kontraktów danych mogą być tworzone automatycznie z istniejących usług przy użyciu narzędzia umowy. Aby użyć narzędzia umowy, plik definicji schematu XML (XSD) musi zostać pobrany lokalnie; narzędzie nie może importować zdalnych kontraktów na dane za pośrednictwem protokołu HTTP.

 Narzędzie umowy pierwszy jest zintegrowany z visual studio 2012 jako zadanie kompilacji. Pliki kodu generowane przez zadanie kompilacji są tworzone za każdym razem, gdy projekt jest zbudowany, dzięki czemu projekt można łatwo przyjąć zmiany w podstawowej umowy serwisowej.

 Typy schematów, które narzędzie umowy po pierwsze można zaimportować, są następujące:

```xml
<xsd:complexType>
 <xsd:simpleType>
 </xsd:simpleType>
</xsd:complexType>
```

 Typy proste nie zostaną wygenerowane, jeśli `Int16` są `String`prymitywami, takimi jak lub ; typy złożone nie zostaną wygenerowane, jeśli są typu `Collection`. Typy również nie zostaną wygenerowane, `xsd:complexType`jeśli są częścią innego . We wszystkich tych przypadkach typy będą odwoływane do istniejących typów w projekcie zamiast tego.

## <a name="adding-a-data-contract-to-a-project"></a>Dodawanie kontraktu danych do projektu
 Przed użyciem narzędzia umowy pierwszy, umowa serwisowa (XSD) należy dodać do projektu. Na potrzeby tego przeglądu, poniższa umowa zostanie wykorzystana do zilustrowania funkcji umowy. Ta definicja usługi jest małym podzbiorem umowy serwisowej używanej przez interfejs API wyszukiwania Bing.

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

 Aby dodać powyższą umowę serwisową do projektu, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj nowy...**. Wybierz opcję Definicja schematu z okienka WCF okna dialogowego Szablony i nazwij nowy plik SampleContract.xsd. Skopiuj i wklej powyższy kod do widoku kodu nowego pliku.

## <a name="configuring-contract-first-options"></a>Konfigurowanie opcji pierwszego kontraktu
 Opcje kontraktu-first można skonfigurować w menu Właściwości projektu WCF. Aby włączyć programowanie oparte na umowie, zaznacz pole wyboru **Włącz XSD jako język definicji typu** na stronie WCF okna właściwości projektu.

 ![Zrzut ekranu przedstawiający opcje WCF z włączonym programem rozwoju pierwszego kontraktu.](./media/contract-first-tool/contract-first-options.png)

 Aby skonfigurować właściwości zaawansowane, kliknij przycisk Zaawansowane.

 ![Okno dialogowe Zaawansowane ustawienia generowania kodu kontraktu.](./media/contract-first-tool/advanced-contract-settings.png)

 Następujące ustawienia zaawansowane można skonfigurować do generowania kodu z kontraktów. Ustawienia można skonfigurować tylko dla wszystkich plików w projekcie; nie można obecnie skonfigurować dla poszczególnych plików.

- **Tryb serializatora:** To ustawienie określa, który serializator jest używany do odczytywania plików umowy serwisowej. Po **wybraniu modułu szeregowego XML** opcje **Typy kolekcji** i **Typy ponownego użycia** są wyłączone. Te opcje dotyczą tylko **serializatora kontraktu danych**.

- **Typy ponownego użycia:** To ustawienie określa, które biblioteki są używane do ponownego użycia typu. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializatora** jest ustawiony na **Serializator kontraktu danych**.

- **Typ kolekcji:** To ustawienie określa w pełni kwalifikowany lub kwalifikowany typ zestawu, który ma być używany dla typu danych zbierania. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializatora** jest ustawiony na **Serializator kontraktu danych**.

- **Typ słownika:** To ustawienie określa w pełni kwalifikowany lub kwalifikowany typ zestawu, który ma być używany dla typu danych słownika.

- **EnableDataBinding**: To ustawienie określa, <xref:System.ComponentModel.INotifyPropertyChanged> czy interfejs ma być implementował wszystkie typy danych w celu zaimplementowania powiązania danych.

- **ExcludedTypes**:To ustawienie określa listę w pełni kwalifikowanych lub kwalifikowanych typów zestawu, które mają zostać wykluczone z zestawów, do których istnieje odwołanie. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializatora** jest ustawiony na **Serializator kontraktu danych**.

- **GenerateInternalTypes**: To ustawienie określa, czy mają być generowane klasy oznaczone jako wewnętrzne. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializatora** jest ustawiony na **Serializator kontraktu danych**.

- **GenerateSerializableTypes**: To ustawienie określa, czy <xref:System.SerializableAttribute> mają być generowane klasy z atrybutem. To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializatora** jest ustawiony na **Serializator kontraktu danych**.

- **ImportXMLTypes**: To ustawienie określa, czy skonfigurować serializator <xref:System.SerializableAttribute> umowy danych, <xref:System.Runtime.Serialization.DataContractAttribute> aby zastosować atrybut do klas bez atrybutu.  To ustawienie ma zastosowanie tylko wtedy, gdy **tryb serializatora** jest ustawiony na **Serializator kontraktu danych**.

- **SupportFx35TypedDataSets**: To ustawienie określa, czy należy zapewnić dodatkowe funkcje dla wpisanych zestawów danych utworzonych dla programu .NET Framework 3.5. Gdy **tryb serializatora** jest ustawiony na <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> **XML Serializer,** rozszerzenie zostanie dodane do importera schematu XML, gdy ta wartość jest ustawiona na True. Gdy **tryb serializatora** jest ustawiony na <xref:System.DateTimeOffset> **Serializator kontraktów danych,** typ zostanie wykluczony z odwołań, gdy ta wartość jest ustawiona na False, tak aby <xref:System.DateTimeOffset> zawsze jest generowany dla starszych wersji frameworka.

- **InputXsdFiles**: To ustawienie określa listę plików wejściowych. Każdy plik musi zawierać prawidłowy schemat XML.

- **Język:** To ustawienie określa język wygenerowanego kodu umowy. Ustawienie musi być rozpoznawalne przez <xref:System.CodeDom.Compiler.CodeDomProvider>.

- **NamespaceMappings**: To ustawienie określa mapowania z obszarów nazw docelowych XSD do obszarów nazw CLR. Każde mapowanie powinno mieć następujący format:

    ```xml
    "Schema Namespace, CLR Namespace"
    ```

     Serializator XML akceptuje tylko jedno mapowanie w następującym formacie:

    ```xml
    "*, CLR Namespace"
    ```

- **OutputDirectory**: To ustawienie określa katalog, w którym będą generowane pliki kodu.

 Ustawienia będą używane do generowania typów umów serwisowych z plików umowy serwisowej podczas tworzenia projektu.

## <a name="using-contract-first-development"></a>Korzystanie z rozwoju pierwszego kontraktu
 Po dodaniu umowy serwisowej do projektu i potwierdzeniu ustawień kompilacji, zbuduj projekt, naciskając **klawisz F6**. Typy zdefiniowane w umowie serwisowej będą następnie dostępne do użycia w projekcie.

 Aby użyć typów zdefiniowanych w umowie serwisowej, dodaj odwołanie do `ContractTypes` bieżącej przestrzeni nazw:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Typy zdefiniowane w umowie serwisowej będą następnie rozwiązywalne w projekcie, jak pokazano poniżej:

 ![SearchRequest klasy wyświetlane w IntelliSense po wpisaniu pierwszych kilku liter.](./media/contract-first-tool/service-contract-types.png)

 Typy generowane przez narzędzie są tworzone w pliku GeneratedXSDTypes.cs. Plik jest tworzony \<w katalogu projektu>/obj/\<build konfiguracji>/XSDGeneratedCode/ katalogu domyślnie. Przykładowy schemat na początku tego artykułu jest konwertowany w następujący sposób:

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
 Błędy i ostrzeżenia napotkane podczas analizowania schematu XSD będą wyświetlane jako błędy kompilacji i ostrzeżenia.

## <a name="interface-inheritance"></a>Dziedziczenie interfejsu
 Nie jest możliwe użycie dziedziczenia interfejsu z rozwojem pierwszego kontraktu; jest to zgodne ze sposobem zachowania interfejsów w innych operacjach. Aby użyć interfejsu, który dziedziczy interfejs podstawowy, należy użyć dwóch oddzielnych punktów końcowych. Pierwszy punkt końcowy używa dziedziczonego kontraktu, a drugi punkt końcowy implementuje interfejs podstawowy.
