---
title: 'Porady: ustawianie poziomu dekompresji JPEG'
description: Dowiedz się, jak dostosować jakość obrazu JPEG, modyfikując jego poziom kompresji na Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
ms.openlocfilehash: 1f6a96e8a05fff40eb08da0ce318faa86a06cc3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618717"
---
# <a name="how-to-set-jpeg-compression-level"></a><span data-ttu-id="1d930-103">Porady: ustawianie poziomu dekompresji JPEG</span><span class="sxs-lookup"><span data-stu-id="1d930-103">How to: Set JPEG Compression Level</span></span>
<span data-ttu-id="1d930-104">Możesz chcieć zmodyfikować parametry obrazu, gdy zapisujesz obraz na dysku w celu zminimalizowania rozmiaru pliku lub poprawy jego jakości.</span><span class="sxs-lookup"><span data-stu-id="1d930-104">You may want to modify the parameters of an image when you save the image to disk to minimize the file size or improve its quality.</span></span> <span data-ttu-id="1d930-105">Jakość obrazu JPEG można dostosować, modyfikując jego poziom kompresji.</span><span class="sxs-lookup"><span data-stu-id="1d930-105">You can adjust the quality of a JPEG image by modifying its compression level.</span></span> <span data-ttu-id="1d930-106">Aby określić poziom kompresji podczas zapisywania obrazu JPEG, należy utworzyć <xref:System.Drawing.Imaging.EncoderParameters> obiekt i przekazać go do <xref:System.Drawing.Image.Save%2A> metody <xref:System.Drawing.Image> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d930-106">To specify the compression level when you save a JPEG image, you must create an <xref:System.Drawing.Imaging.EncoderParameters> object and pass it to the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="1d930-107">Zainicjuj <xref:System.Drawing.Imaging.EncoderParameters> obiekt, aby miał tablicę składającą się z jednego <xref:System.Drawing.Imaging.EncoderParameter> .</span><span class="sxs-lookup"><span data-stu-id="1d930-107">Initialize the <xref:System.Drawing.Imaging.EncoderParameters> object so that it has an array that consists of one <xref:System.Drawing.Imaging.EncoderParameter>.</span></span> <span data-ttu-id="1d930-108">Podczas tworzenia <xref:System.Drawing.Imaging.EncoderParameter> , określ <xref:System.Drawing.Imaging.Encoder.Quality> koder i żądany poziom kompresji.</span><span class="sxs-lookup"><span data-stu-id="1d930-108">When you create the <xref:System.Drawing.Imaging.EncoderParameter>, specify the <xref:System.Drawing.Imaging.Encoder.Quality> encoder, and the desired compression level.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d930-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d930-109">Example</span></span>  
 <span data-ttu-id="1d930-110">Poniższy przykładowy kod tworzy <xref:System.Drawing.Imaging.EncoderParameter> obiekt i zapisuje trzy obrazy JPEG.</span><span class="sxs-lookup"><span data-stu-id="1d930-110">The following example code creates an <xref:System.Drawing.Imaging.EncoderParameter> object and saves three JPEG images.</span></span> <span data-ttu-id="1d930-111">Każdy obraz JPEG jest zapisywany z innym poziomem jakości przez zmodyfikowanie `long` wartości przesłanej do <xref:System.Drawing.Imaging.EncoderParameter> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1d930-111">Each JPEG image is saved with a different quality level, by modifying the `long` value passed to the <xref:System.Drawing.Imaging.EncoderParameter> constructor.</span></span> <span data-ttu-id="1d930-112">Poziom jakości równy 0 odpowiada najwyższej kompresji, a poziom jakości 100 odpowiada najmniej kompresji.</span><span class="sxs-lookup"><span data-stu-id="1d930-112">A quality level of 0 corresponds to the greatest compression, and a quality level of 100 corresponds to the least compression.</span></span>  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d930-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1d930-113">Compiling the Code</span></span>  
 <span data-ttu-id="1d930-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1d930-114">This example requires:</span></span>  
  
- <span data-ttu-id="1d930-115">Aplikacja Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1d930-115">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="1d930-116">A <xref:System.Windows.Forms.PaintEventArgs> , który jest parametrem <xref:System.Windows.Forms.PaintEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="1d930-116">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
- <span data-ttu-id="1d930-117">Plik obrazu o nazwie `TestPhoto.jpg` i zlokalizowany w **c \\ :**.</span><span class="sxs-lookup"><span data-stu-id="1d930-117">An image file that is named `TestPhoto.jpg` and located at **c:\\**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d930-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d930-118">See also</span></span>

- [<span data-ttu-id="1d930-119">Porady: określanie parametrów obsługiwanych przez koder</span><span class="sxs-lookup"><span data-stu-id="1d930-119">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)
- [<span data-ttu-id="1d930-120">Typy map bitowych</span><span class="sxs-lookup"><span data-stu-id="1d930-120">Types of Bitmaps</span></span>](types-of-bitmaps.md)
- [<span data-ttu-id="1d930-121">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="1d930-121">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
