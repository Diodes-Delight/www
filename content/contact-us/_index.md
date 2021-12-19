---
title: "Contact"
menu:
    main:
        weight: 99
layout: docs
---

{{< blocks/lead >}}
<h2>Get in touch</h2>
<h3>Looking for technical support? Then please visit our {{% url data=discord title=Discord %}} first.</h3>
<h3>For all other inquiries please use the form below.</h3>
{{< /blocks/lead >}}


<form id="contact-form" method="post" action="https://formspree.io/f/xyylplyk" role="form" style="margin-top:10%">
    <div class="col-md-8 mx-auto">
    Contact details:

- Company name: Diodes Delight
- E-mail: contact@diodes-delight.com

Diodes Delight is not doing business with end-consumers. Please contact the distributor you purchased your hardware from if you have questions about returns or warranty.
    </div>
    <div class="controls">
        <div class="row">
            <div class="col-md-8 mx-auto">
                <div class="form-group">
                    <input id="form_name" type="text" name="name" class="form-control" placeholder="Name" required="required">
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-md-8 mx-auto">
                <div class="form-group">
                    <input id="form_email" type="text" name="email" class="form-control" placeholder="Email" required="required">
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-md-8 mx-auto">
                <div class="form-group">
                    <textarea id="form_message" name="message" class="form-control" placeholder="Message" rows="4" required="required"></textarea>
                </div>
            </div>
            <div class="col-md-8 mx-auto">
                <input type="submit" class="btn btn-success btn-send" value="Submit">
            </div>
        </div>
    </div>
</form>


{{< blocks/section type="section" color="white">}}


{{< /blocks/section >}}
