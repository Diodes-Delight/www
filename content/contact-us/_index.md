---
title: "Contact"
menu:
    main:
        weight: 99
layout: docs
---

{{< blocks/lead >}}
<h2>Get in touch with us!</h2>
<h3>Looking for technical support? Then please visit our {{% url data=discord title=Discord %}} first.</h3>
<h3>For project inquiries please use the form below.</h3>
<br>
<h5>Please note that Diodes Delight is not selling products directly to end-consumers. If you have questions about returns or warranty then please contact the distributor you purchased your hardware from.</h5>
{{< /blocks/lead >}}


<form id="contact-form" method="post" action="https://formspree.io/f/xyylplyk" role="form" style="margin-top:10%">
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
            <div class="g-recaptcha" data-sitekey="6LeC8xkkAAAAAB27zJurqyz6_mXaJ7CQe54h5N_C"></div>
            <div class="col-md-8 mx-auto">
                <input type="submit" class="btn btn-success btn-send" value="Submit">
            </div>
        </div>
    </div>
</form>


{{< blocks/section type="section" color="white">}}


{{< /blocks/section >}}
