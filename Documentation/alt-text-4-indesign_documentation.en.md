# Alt-text-4-InDesign – Documentation

The *Alt-text-4-InDesign* plug-in is designed to help you create alternative texts for images and graphics in *Adobe InDesign*.

## Installation

Installation is done via the Adobe Creative Cloud application (Stock and Marketplace) or [Adobe Exchange](https://exchange.adobe.com/apps/cc/1c6b7a83/alt-text-for-indesign). Updates can also be installed via this application. 

## License

The license purchased via Adobe Exchange (Stock and Marketplace) is a single user license. The cost of requests to the large language models (LLMs) from *OpenAI*, *Google*, or *Mistral AI* is included in the plugin price. (Fair Use Policy) Inquiries regarding an Enterprise license to [roland.dreger@ik.me](mailto:roland.dreger@ik.me).

The license key is entered in the `Settings` tab of the panel.

## Alternate Text

Alternative text, also known as ALT text, is an essential component of accessible documents. It is used to describe non-textual content such as images or graphics and can be read and reproduced by assistive technologies such as screen readers.

If an image is selected in the open InDesign document, the plugin reads the alternate text from the object export options. (Object → Object export options ... → Alternate text) If a text is available, it is displayed in the `Images` tab of the plugin panel in the top input field. You can also change the alternative text directly via the input field for the selected object.

If no alternative text is stored, you can insert one using the input field in the panel. To do so, activate the checkbox `Custom Alt-text` and enter the desired text in the field. This is then applied as the alternative text for the selected object.

[Preview Alt-text generation on vimeo](https://vimeo.com/1026952093)

A suggestion for an alternate text can be created using the `Generate` button. The generation is based on a Large Language Model (LLM) from *OpenAI*, *Google* or *Mistral AI*. Please note that language models can make mistakes. Therefore, check the suggested texts and do not enter any sensitive data in the prompt input field, for example no personal or confidential data.

An existing text in the ALT text field (top input field in the plugin panel) provides the context for the generation of the (new) ALT text. This is helpful, for example, if a specific region for a landscape photo or the name of a celebrity in a photo is to be included in the description of the content.

### Image Navigation

The arrow buttons below the alternative text input field are used to navigate within the active document:

`«`   First image in document  
`‹`   Previous image  
`›`   Next image  
`»`   Last image in document  

### Object indicator

Between the image navigation buttons you will find an object indicator. This indicator shows whether the current selection is an image, a group, or a mathematical expression (MathML). 

Why is this distinction important? Depending on the object type, PDF and ePub export can lead to different results when assigning ALT text.

For example, when exporting a group of image frames to PDF, the alternative text for that group is used rather than the alternative text for the individual images. When exporting to ePub, the opposite is true. If both the group and the grouped images have alternative texts, only the ALT text of the individual images and not that of the group is included in the ePub document. There are also differences when exporting mathematical expressions.

### Update Metadata (XMP)

You can use the refesh `XMP` button to edit the metadata (XMP) of the linked image file. 

**Modified entry**: *Alt Text (Accessibility)* in the *IPTC Content* section of the XMP metadata.  
**Inserted Value**: The current entry in the `Alternate Text` input field in the plugin panel, *Image* tab.

In the *Alt Text (Accessibility)* entry, entries in multiple languages are possible in addition to the default language (*x-default*). If you want to work with different languages, enable the `Multiple Languages` option in the settings under the *Metadata (XMP)* section. Otherwise, leave this option disabled, and only the default value will be added, modified, or removed.

**Note**: You can also delete the *Alt Text (Accessibility)* entry from the file’s metadata. To do so, leave the `Alternative Text` input field in the plugin panel blank and click the refesh `XMP` button in the metadata section. If the `Multiple Languages` option is enabled in the settings, the entry for the language of the alternative text will be deleted. If the option is disabled, the entire *Alt Text (Accessibility)* entry will be removed from the file’s metadata.

### Prompt

An instruction (prompt) for the LLM is predefined for the automated generation of the alternative text. You can adapt this prompt suggestion or enter it from scratch. To do this, activate the checkbox `Alt-text instructions` in the footer of the panel. This will display an additional input field.

**Note:** The input also affects the automatic generation of alternative texts for all linked images.

#### Selection

Using the menu above the prompt input field, you can select pre-installed prompts (in square brackets) and your own prompts. 

To save your own prompt, enter your text in the prompt input field. Click on the `Save` icon to the right above the input field. Choose an individual name for it. Your prompts will then be available for ALT text generation even after restarting InDesign. 

**Note**: Please keep a backup of your own prompts so that you can restore them if necessary. Permanent storage in the plugin cannot be guaranteed under all circumstances, e.g., if InDesign or the plugin is reinstalled.

#### Language

It may happen that the language of your InDesign user interface does not match the document language, i.e. the language in which the alternate texts are to be generated. In this case, you can specify a specific language. To do this, select the desired target language from the drop-down menu on the right above the prompt input field. The following are available: Afrikaans, Catalan, Danish, German, English, Spanish, French, Hindi, Italian, Korean and Swedish.

If the prompt input field with the dropdown for the language selection is not visible, activate the checkbox `Alt-text instructions` in the footer of the panel.

**Note:** The setting also affects the automatic generation of alternate texts for all linked images.

### Source for Alternate Text

The source for the alternate text can be specified above the input field for the alternate text, for example if the alternative text is to be inserted from the object's metadata (XMP). To do this, use the `Source` drop-down menu on the right above the input field.

## Context

- `ALT-Text` The currently available alternative text is used as context—that is, the entire text visible in the `Alternative Text` field in the panel. 

However, instead of using the existing alternative text, you can also enter additional information into this input field. Examples include the name of a person if they are to be identified, or the location depicted. 

The intended use of the image is also important when creating alternative text. This can be specified more precisely by entering keywords in this field.

- `Page` The entire text of the page on which the image is placed.

- `Article` The surrounding text of the image is used as context. In the case of an anchored object, this corresponds to the story in which the image is anchored. Specifically, a few paragraphs before and after the image’s position are evaluated. If the image is not anchored but is part of an article (InDesign → Window → Article), the text of the article entries is read, and a few paragraphs before and after the image are used to generate the alternative text.

- `Metadata` The metadata from the linked image file are used as context. The following metadata are evaluated: **Document Title** (dc:title), **Description** *(dc:description)*, **Keywords** *(dc:subject)*, **Headline** *(photoshop:Headline)*, **Alt Text** *(Iptc4xmpCore:AltTextAccessibility)*, and **Extended Description** *(Iptc4xmpCore:ExtDescrAccessibility)*.

## PDF with Tags

You can also use the panel to change the options for exporting PDFs with a tag structure, including an input option for actual text or marking an object as an artefact.

### Actual Text

Actual text is used to describe text that is visually perceived as text but is not encoded as such. A typical example is an image that represents a single word or a vector object that represents a single character. 

The actual text makes it possible to link the text perceived by sighted users to the corresponding objects. This additional text-based representation of the content can be used by screen readers or other assistive technologies. 

If the input field for the actual text is not visible, activate the checkbox `PDF with tags` in the footer area of the panel.

### Source for Actual Text

The source for the actual text can be specified above the input field. To do this, use the drop-down menu `Source` on the right above the input field.

### Artefacts

The option `Decorative element (no PDF tag)` is always visible. If this checkbox is activated, the selected object is marked as a decorative element (non-text element) in the InDesign document. This object therefore does not appear in the tag structure in the exported PDF file.

The object marked in this way is also marked as a decorative element for ePub or HTML. In the exported ePub or HTML document, this element is assigned an empty alt attribute (i.e. alt=“”) and is therefore ignored by assistive technologies (e.g. screen readers).

## Metadata

Starting with version 2.2 of the plugin, an additional `Metadata` tab is available in the panel. This tab displays the metadata for the selected image. If an entry is empty or cannot be read in InDesign, a replacement dash (–) is displayed.

The following metadata fields are evaluated: **Document Title** (dc:title), **Description** *(dc:description)*, **Keywords** *(dc:subject)*, **Headline** *(photoshop:Headline)*, **Alt Text** *(Iptc4xmpCore:AltTextAccessibility)*, **Extended Description** *(Iptc4xmpCore:ExtDescrAccessibility)*. This metadata will be included as context for generating the alternative text, if the option for this is selected. (see above)

## Settings
### License Key

In the `Settings` tab, you can enter the license key that you got when you purchased the plug-in.

### ALT text creation
#### AI providers

You can choose between two AI providers for the generation of alternative texts:

- **OpenAI** is a U.S. software company based in San Francisco. Use OpenAI for general subjects and concise alternative text.
- **Google** is a U.S. software company based in California. Google is particularly good at object recognition, even for unusual subjects.
- **Mistral AI** is a French software company based in Paris. Choose Mistral AI if it’s important to you that your image data are processed in Europe.

The setting you choose will remain in place even after restarting InDesign.

### Metadata (XMP)
#### Update in Image File

**Multiple Languages**: With this option, you can choose whether the ALT text should be inserted into the image file's metadata (XMP) only for the default value (x-default) or for multiple languages (en, de, fr, ...). This setting also applies to the deletion process if the input field for the alternative text in the *Image* tab is empty.

If this option is enabled, a drop-down menu appears for selecting the default language. The ALT text for the language selected here is used as the entry for the *x-default* language in the metadata.

### Automated Actions
#### Generating custom ALT texts for images

The `Generate all` action automatically **assigns an custom alternative text** to all objects with links. Links whose InDesign object is marked as a decorative image or non-text element are skipped. 

A Large Language Model (LLM) from *OpenAI*, *Google* or *Mistral AI* is used to create the alternative texts. The images are processed using the providers' API. The specifications for the generation instruction (prompt), the target language or the context are taken from the settings in the panel. If the prompt input field and the drop-down menu for the language selection are not visible, activate the checkbox `Instruction for ALT text` in the footer of the panel.

In the `Settings` tab, you can make **additional settings for automated Alt-text generation** in the `Automated actions` section. Here you can specify whether to overwrite existing alternative text, whether to process the active document or all documents, and whether to include images on hidden layers or on the pasteboard.

#### Creating Custom ALT Texts for Mathematical Expressions

The `ALT Texts for MathML` action automatically **creates** **custom alternative texts** for all (InDesign-native) mathematical expressions. Mathematical expressions marked as decorative images or non-text elements are skipped.

The target language is taken from the setting in the panel. If the drop-down menu for language selection is not visible, check the `ALT Text Instruction` checkbox at the bottom of the panel.

In the `Settings` tab, under the `Automated Actions` section, you can configure **additional settings for automated ALT text generation**. Here, you can specify whether to overwrite existing alternative text, whether to process the active document or all documents, and whether to include mathematical expressions on hidden layers or the artboard.

#### Removing custom ALT texts

The `Remove all` action **removes the custom alternate text** for all objects. Entries for actual text remain unchanged. The values for the `Source for Actual Text` option are not altered by this action.

In the `Settings` tab, you can make **additional settings for automatically removing alternative text** in the `Automated actions` section. Here you can specify whether to process the active document or all documents, and whether to include hidden images or images on the pasteboard.

#### Update Metadata for Linked Files

The `Update Metadata` action automatically **updates** the metadata in the files for all objects with links.

**Changed entry**: *Alt Text (Accessibility)* in the *IPTC Content* section of the XMP metadata.
**Inserted value**: Current entry in the object’s export options. (Source for alternative text: Custom)

In the *Alt Text (Accessibility)* entry, entries in multiple languages are possible in addition to the default language (*x-default*). If you want to work with different languages, enable the `Multiple Languages` option in the settings under the *Metadata (XMP)* section. Otherwise, leave this option disabled, and only the default value will be added or modified.

In the `Settings` tab, under the `Automated Actions` section, you can configure **additional settings for updating metadata**. Here, you can specify whether to overwrite existing metadata, whether to process the active document or all documents, and whether to include hidden images or images on the artboard.

## Questions and support

[roland.dreger@ik.me](mailto:roland.dreger@ik.me)