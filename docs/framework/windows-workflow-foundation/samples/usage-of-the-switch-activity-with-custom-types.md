---
title: Użycie działania Switch z typami niestandardowymi
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: b24a03573b31f3fb1c34d4aa6e03bc11f5b25455
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038877"
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Użycie działania Switch z typami niestandardowymi
W tym przykładzie opisano sposób włączania <xref:System.Activities.Statements.Switch%601> działanie, aby ocenić zdefiniowanych przez użytkownika typem złożonym w czasie wykonywania. W procedurach tradycyjnych językach programowania [Przełącz](https://go.microsoft.com/fwlink/?LinkId=180521) instrukcja wybiera logiki wykonywania na podstawie oceny warunkowego zmiennej. Tradycyjnie `switch` instrukcji operuje na wyrażenie, które może przyjąć statycznie. Na przykład w języku C# oznacza to, że tylko prymitywnymi typami, takich jak <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, oraz typy wyliczeniowe są obsługiwane.  
  
 Aby włączyć przełączanie na klasę niestandardową, logiki należy zaimplementować pozwala obliczyć wartości niestandardowego typu złożonego w czasie wykonywania. W tym przykładzie pokazano, jak włączyć przełączania na niestandardowy typ złożony, o nazwie `Person`.  
  
-   Klasy niestandardowe `Person`, <xref:System.ComponentModel.TypeConverter> atrybut jest zadeklarowany za pomocą nazwę niestandardowej <xref:System.ComponentModel.TypeConverter>.  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   Klasy niestandardowe `Person`, <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> klasy zostaną zastąpione.  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   Niestandardowy <xref:System.ComponentModel.TypeConverter> zaimplementowaniu klasy, który wykonuje konwersję wystąpienia klasy niestandardowego ciągu i ciąg na wystąpienie klasy niestandardowej.  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 W tym przykładzie są uwzględnione następujące pliki:  
  
-   **Osoba.cs**: definiuje `Person` klasy.  
  
-   **PersonConverter.cs**: konwerter typów dla `Person` klasy.  
  
-   **Sequence.XAML**: przepływ pracy, który przełącza `Person` typu.  
  
-   **Plik program.cs**: główna funkcja, która uruchamia przepływ pracy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Ładowanie Switch.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić przykład.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowana biblioteka działań](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
