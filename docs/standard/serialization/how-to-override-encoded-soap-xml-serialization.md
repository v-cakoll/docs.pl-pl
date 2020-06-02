---
title: 'Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP'
description: Dowiedz się więcej na temat zastępowania serializacji XML obiektów jako komunikatów SOAP, co przypomina proces przesłaniania standardowej serializacji XML.
ms.date: 03/30/2017
helpviewer_keywords:
- overriding XML serialization
- SOAP, overriding encoded XML serialization
ms.assetid: d0791df8-04e3-46b4-a6be-fe0ed09267e8
ms.openlocfilehash: 50688cb25294f14a9dd4596258eb95adf93cdb41
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277989"
---
# <a name="how-to-override-encoded-soap-xml-serialization"></a><span data-ttu-id="f2b1c-103">Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="f2b1c-103">How to: Override Encoded SOAP XML Serialization</span></span>

<span data-ttu-id="f2b1c-104">Zastępowanie serializacji obiektów XML jako komunikaty protokołu SOAP proces jest podobny do procesu dla zastępowanie standardowych serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-104">The process for overriding XML serialization of objects as SOAP messages is similar to the process for overriding standard XML serialization.</span></span> <span data-ttu-id="f2b1c-105">Aby uzyskać informacje na temat zastępowania standardowej serializacji XML, zobacz [How to: Określanie alternatywnej nazwy elementu dla strumienia XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span><span class="sxs-lookup"><span data-stu-id="f2b1c-105">For information about overriding standard XML serialization, see [How to: Specify an Alternate Element Name for an XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>

## <a name="to-override-serialization-of-objects-as-soap-messages"></a><span data-ttu-id="f2b1c-106">Aby zastąpić serializacji obiektów jako protokołu SOAP wiadomości</span><span class="sxs-lookup"><span data-stu-id="f2b1c-106">To override serialization of objects as SOAP messages</span></span>

1. <span data-ttu-id="f2b1c-107">Utworzenie wystąpienia <xref:System.Xml.Serialization.SoapAttributeOverrides> klasy.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-107">Create an instance of the <xref:System.Xml.Serialization.SoapAttributeOverrides> class.</span></span>

2. <span data-ttu-id="f2b1c-108">Utwórz `SoapAttributes` dla każdej składowej klasy, która jest deserializowana.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-108">Create a `SoapAttributes` for each class member that is being serialized.</span></span>

3. <span data-ttu-id="f2b1c-109">Utworzenie wystąpienia co najmniej jeden z atrybutów, które wpływa na serializacji XML, odpowiednio do elementu członkowskiego serializowanego.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-109">Create an instance of one or more of the attributes that affect XML serialization, as appropriate, to the member being serialized.</span></span> <span data-ttu-id="f2b1c-110">Aby uzyskać więcej informacji zobacz "Atrybuty czy kontroli kodowany protokołu SOAP serializacji".</span><span class="sxs-lookup"><span data-stu-id="f2b1c-110">For more information, see "Attributes That Control Encoded SOAP Serialization".</span></span>

4. <span data-ttu-id="f2b1c-111">Ustaw odpowiednią właściwość `SoapAttributes` dla atrybutu, który został utworzony w kroku 3.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-111">Set the appropriate property of `SoapAttributes` to the attribute created in step 3.</span></span>

5. <span data-ttu-id="f2b1c-112">Add `SoapAttributes` to `SoapAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-112">Add `SoapAttributes` to `SoapAttributeOverrides`.</span></span>

6. <span data-ttu-id="f2b1c-113">Utwórz `XmlTypeMapping` za pomocą `SoapAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-113">Create an `XmlTypeMapping` using the `SoapAttributeOverrides`.</span></span> <span data-ttu-id="f2b1c-114">Użyj metody `SoapReflectionImporter.ImportTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-114">Use the `SoapReflectionImporter.ImportTypeMapping` method.</span></span>

7. <span data-ttu-id="f2b1c-115">Utwórz `XmlSerializer` za pomocą `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-115">Create an `XmlSerializer` using `XmlTypeMapping`.</span></span>

8. <span data-ttu-id="f2b1c-116">Serializacji lub deserializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-116">Serialize or deserialize the object.</span></span>

## <a name="example"></a><span data-ttu-id="f2b1c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2b1c-117">Example</span></span>

<span data-ttu-id="f2b1c-118">Poniższy przykład kodu serializacji plik na dwa sposoby: najpierw, bez zastępowania `XmlSerializer` zachowania klasy i sekundy, przez zastąpienie zachowania.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-118">The following code example serializes a file in two ways: first, without overriding the `XmlSerializer` class's behavior, and second, by overriding the behavior.</span></span> <span data-ttu-id="f2b1c-119">Przykład zawiera klasę o nazwie `Group` z kilkoma elementami członkowskimi.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-119">The example contains a class named `Group` with several members.</span></span> <span data-ttu-id="f2b1c-120">`SoapElementAttribute`Do elementów członkowskich klasy zastosowano różne atrybuty, takie jak.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-120">Various attributes, such as the `SoapElementAttribute`, have been applied to class members.</span></span> <span data-ttu-id="f2b1c-121">Gdy klasa jest serializowana z `SerializeOriginal` metody atrybuty kontrolować zawartość komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f2b1c-121">When the class is serialized with the `SerializeOriginal` method, the attributes control the SOAP message content.</span></span> <span data-ttu-id="f2b1c-122">Gdy `SerializeOverride` jest wywoływana metoda, zachowanie `XmlSerializer` zostanie zastąpiona przez tworzenie różnych atrybutów i ustawienie właściwości `SoapAttributes` do tych atrybutów (zgodnie z potrzebami).</span><span class="sxs-lookup"><span data-stu-id="f2b1c-122">When the `SerializeOverride` method is called, the behavior of the `XmlSerializer` is overridden by creating various attributes and setting the properties of a `SoapAttributes` to those attributes (as appropriate).</span></span>

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;
using System.Xml.Schema;

public class Group
{
    [SoapAttribute (Namespace = "http://www.cpandl.com")]
    public string GroupName;

    [SoapAttribute(DataType = "base64Binary")]
    public Byte [] GroupNumber;

    [SoapAttribute(DataType = "date", AttributeName = "CreationDate")]
    public DateTime Today;
    [SoapElement(DataType = "nonNegativeInteger", ElementName = "PosInt")]
    public string PositiveInt;
    // This is ignored when serialized unless it is overridden.
    [SoapIgnore]
    public bool IgnoreThis;

    public GroupType Grouptype;

    [SoapInclude(typeof(Car))]
    public Vehicle myCar(string licNumber)
    {
        Vehicle v;
        if(licNumber == "")
            {
                v = new Car();
            v.licenseNumber = "!!!!!!";
        }
        else
        {
            v = new Car();
            v.licenseNumber = licNumber;
        }
        return v;
    }
}

public abstract class Vehicle
{
    public string licenseNumber;
    public DateTime makeDate;
}

public class Car: Vehicle
{
}

public enum GroupType
{
    // These enums can be overridden.
    small,
    large
}

public class Run
{
    public static void Main()
    {
        Run test = new Run();
        test.SerializeOriginal("SoapOriginal.xml");
        test.SerializeOverride("SoapOverrides.xml");
        test.DeserializeOriginal("SoapOriginal.xml");
        test.DeserializeOverride("SoapOverrides.xml");

    }
    public void SerializeOriginal(string filename)
    {
        // Creates an instance of the XmlSerializer class.
        XmlTypeMapping myMapping =
        (new SoapReflectionImporter().ImportTypeMapping(
        typeof(Group)));
        XmlSerializer mySerializer =
        new XmlSerializer(myMapping);

        // Writing the file requires a TextWriter.
        TextWriter writer = new StreamWriter(filename);

        // Creates an instance of the class that will be serialized.
        Group myGroup = new Group();

        // Sets the object properties.
        myGroup.GroupName = ".NET";

        Byte [] hexByte = new Byte[2]{Convert.ToByte(100),
        Convert.ToByte(50)};
        myGroup.GroupNumber = hexByte;

        DateTime myDate = new DateTime(2002,5,2);
        myGroup.Today = myDate;

        myGroup.PositiveInt= "10000";
        myGroup.IgnoreThis=true;
        myGroup.Grouptype= GroupType.small;
        Car thisCar =(Car)  myGroup.myCar("1234566");

        // Prints the license number just to prove the car was created.
        Console.WriteLine("License#: " + thisCar.licenseNumber + "\n");

        // Serializes the class and closes the TextWriter.
        mySerializer.Serialize(writer, myGroup);
        writer.Close();
    }

    public void SerializeOverride(string filename)
    {
        // Creates an instance of the XmlSerializer class
        // that overrides the serialization.
        XmlSerializer overRideSerializer = CreateOverrideSerializer();

        // Writing the file requires a TextWriter.
        TextWriter writer = new StreamWriter(filename);

        // Creates an instance of the class that will be serialized.
        Group myGroup = new Group();

        // Sets the object properties.
        myGroup.GroupName = ".NET";

        Byte [] hexByte = new Byte[2]{Convert.ToByte(100),
        Convert.ToByte(50)};
        myGroup.GroupNumber = hexByte;

        DateTime myDate = new DateTime(2002,5,2);
        myGroup.Today = myDate;

        myGroup.PositiveInt= "10000";
        myGroup.IgnoreThis=true;
        myGroup.Grouptype= GroupType.small;
        Car thisCar =(Car)  myGroup.myCar("1234566");

        // Serializes the class and closes the TextWriter.
        overRideSerializer.Serialize(writer, myGroup);
         writer.Close();
    }

    public void DeserializeOriginal(string filename)
    {
        // Creates an instance of the XmlSerializer class.
        XmlTypeMapping myMapping =
        (new SoapReflectionImporter().ImportTypeMapping(
        typeof(Group)));
        XmlSerializer mySerializer =
        new XmlSerializer(myMapping);

        TextReader reader = new StreamReader(filename);

        // Deserializes and casts the object.
        Group myGroup;
        myGroup = (Group) mySerializer.Deserialize(reader);

        Console.WriteLine(myGroup.GroupName);
        Console.WriteLine(myGroup.GroupNumber[0]);
        Console.WriteLine(myGroup.GroupNumber[1]);
        Console.WriteLine(myGroup.Today);
        Console.WriteLine(myGroup.PositiveInt);
        Console.WriteLine(myGroup.IgnoreThis);
        Console.WriteLine();
    }

    public void DeserializeOverride(string filename)
    {
        // Creates an instance of the XmlSerializer class.
        XmlSerializer overRideSerializer = CreateOverrideSerializer();
        // Reading the file requires a TextReader.
        TextReader reader = new StreamReader(filename);

        // Deserializes and casts the object.
        Group myGroup;
        myGroup = (Group) overRideSerializer.Deserialize(reader);

        Console.WriteLine(myGroup.GroupName);
        Console.WriteLine(myGroup.GroupNumber[0]);
        Console.WriteLine(myGroup.GroupNumber[1]);
        Console.WriteLine(myGroup.Today);
        Console.WriteLine(myGroup.PositiveInt);
        Console.WriteLine(myGroup.IgnoreThis);
    }

    private XmlSerializer CreateOverrideSerializer()
    {
        SoapAttributeOverrides mySoapAttributeOverrides =
        new SoapAttributeOverrides();
        SoapAttributes soapAtts = new SoapAttributes();

        SoapElementAttribute mySoapElement = new SoapElementAttribute();
        mySoapElement.ElementName = "xxxx";
        soapAtts.SoapElement = mySoapElement;
        mySoapAttributeOverrides.Add(typeof(Group), "PositiveInt",
        soapAtts);

        // Overrides the IgnoreThis property.
        SoapIgnoreAttribute myIgnore = new SoapIgnoreAttribute();
        soapAtts = new SoapAttributes();
        soapAtts.SoapIgnore = false;
        mySoapAttributeOverrides.Add(typeof(Group), "IgnoreThis",
        soapAtts);

        // Overrides the GroupType enumeration.
        soapAtts = new SoapAttributes();
        SoapEnumAttribute xSoapEnum = new SoapEnumAttribute();
        xSoapEnum.Name = "Over1000";
        soapAtts.SoapEnum = xSoapEnum;

        // Adds the SoapAttributes to the
        // mySoapAttributeOverrides.
        mySoapAttributeOverrides.Add(typeof(GroupType), "large",
        soapAtts);

        // Creates a second enumeration and adds it.
        soapAtts = new SoapAttributes();
        xSoapEnum = new SoapEnumAttribute();
        xSoapEnum.Name = "ZeroTo1000";
        soapAtts.SoapEnum = xSoapEnum;
        mySoapAttributeOverrides.Add(typeof(GroupType), "small",
        soapAtts);

        // Overrides the Group type.
        soapAtts = new SoapAttributes();
        SoapTypeAttribute soapType = new SoapTypeAttribute();
        soapType.TypeName = "Team";
        soapAtts.SoapType = soapType;
        mySoapAttributeOverrides.Add(typeof(Group),soapAtts);

        // Creates an XmlTypeMapping that is used to create an instance
        // of the XmlSerializer class. Then returns the XmlSerializer.
        XmlTypeMapping myMapping = (new SoapReflectionImporter(
        mySoapAttributeOverrides)).ImportTypeMapping(typeof(Group));

        XmlSerializer ser = new XmlSerializer(myMapping);
        return ser;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f2b1c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2b1c-123">See also</span></span>

- [<span data-ttu-id="f2b1c-124">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="f2b1c-124">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="f2b1c-125">Atrybuty kontrolujące zakodowaną serializację protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="f2b1c-125">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="f2b1c-126">Serializacji XML za pomocą usług sieci Web XML</span><span class="sxs-lookup"><span data-stu-id="f2b1c-126">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="f2b1c-127">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="f2b1c-127">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="f2b1c-128">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="f2b1c-128">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="f2b1c-129">Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="f2b1c-129">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
