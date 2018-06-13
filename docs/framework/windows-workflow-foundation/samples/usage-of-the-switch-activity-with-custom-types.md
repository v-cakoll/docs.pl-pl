---
title: Użycie działanie Switch z niestandardowych typów
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: 2b6f3109324064cb5e746de9c61e5a70c4c4d60b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517884"
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Użycie działanie Switch z niestandardowych typów
W tym przykładzie opisano, jak włączyć <xref:System.Activities.Statements.Switch%601> działanie, aby ocenić typu złożonego zdefiniowane przez użytkownika w czasie wykonywania. W procedurach najbardziej tradycyjnych językach programowania [przełącznika](http://go.microsoft.com/fwlink/?LinkId=180521) instrukcja wybiera logiki wykonywania oparte na ocenie warunkowy zmiennej. Tradycyjnie `switch` instrukcji działa na wyrażenie, które może przyjąć statycznie. Na przykład w języku C# to oznacza, że typy tego tylko pierwotne, takie jak <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, i typy wyliczeniowe są obsługiwane.  
  
 Umożliwia włączenie klasy niestandardowej logiki musi być implementowana pozwala obliczyć wartości typu złożonego niestandardowych w czasie wykonywania. W tym przykładzie pokazano, jak włączyć włączenie niestandardowego typu złożonego o nazwie `Person`.  
  
-   W niestandardowej klasy `Person`, <xref:System.ComponentModel.TypeConverter> zadeklarowano atrybutu o nazwie niestandardowego <xref:System.ComponentModel.TypeConverter>.  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   W niestandardowej klasy `Person`, <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> klasy zostaną zastąpione.  
  
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
  
-   Niestandardowy <xref:System.ComponentModel.TypeConverter> zaimplementowana jest klasa, która przeprowadza konwersję wystąpienia klasy niestandardowego ciągu i ciąg do wystąpienia klasy niestandardowej.  
  
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
  
 Następujące pliki znajdują się w tym przykładzie:  
  
-   **Person.cs**: definiuje `Person` klasy.  
  
-   **PersonConverter.cs**: konwerter typów dla `Person` klasy.  
  
-   **Sequence.XAML**: przepływ pracy, który przełącza `Person` typu.  
  
-   **Plik program.cs**: funkcja main, która uruchamia przepływ pracy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Ładowanie Switch.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić przykład.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowana biblioteka działań](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
