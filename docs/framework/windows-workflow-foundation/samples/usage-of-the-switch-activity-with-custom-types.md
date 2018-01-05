---
title: "Użycie działanie Switch z niestandardowych typów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61485a59ae3af17bef58c0fccbe062c8b9171a34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowana biblioteka działań](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
